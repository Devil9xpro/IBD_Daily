# Requirements Document

## Introduction

This document defines the requirements for enhancing the existing "IBD Daily Chart" PineScript v6 indicator to consolidate multiple IBD (Investor's Business Daily) methodology tools into a single overlay indicator. The goal is to maximize the analytical capability available within TradingView's free-tier limitation of 2 indicators per chart. The enhanced indicator combines volume analysis, relative strength tracking, pattern detection, and key price levels alongside the existing HLC bars and moving averages.

## Glossary

- **Indicator**: The PineScript v6 overlay indicator named "IBD Daily Chart Enhanced"
- **HLC_Bar**: A price bar displaying High, Low, and Close without an open tick, colored black for up days and red for down days per IBD chart style
- **Volume_Pane**: A separate pane rendered below the price chart displaying volume bars and their moving average
- **RS_Line**: A Relative Strength line calculated by dividing the stock's closing price by the benchmark index closing price, normalized and plotted as an overlay
- **RS_New_High_Dot**: A blue dot marker plotted when the RS_Line makes a new 52-week high
- **Benchmark_Index**: A configurable ticker symbol (default: SPY) used as the denominator in the relative strength calculation
- **Volume_MA**: A 50-day simple moving average of volume, plotted as a line over the volume bars
- **Consolidation_Detector**: A component that identifies flat base and cup-with-handle price patterns
- **Flat_Base**: A consolidation pattern where price trades within a range of 15% or less from high to low over a minimum of 5 weeks (25 trading days)
- **Cup_With_Handle**: A consolidation pattern consisting of a U-shaped price decline and recovery (the cup) followed by a smaller downward drift (the handle), with total depth not exceeding 33% from the left-side high
- **Pivot_Point**: The highest price in the handle of a cup-with-handle pattern or the left-side high of a flat base, representing the ideal buy point
- **Fifty_Two_Week_High**: The highest closing price over the trailing 252 trading days

## Requirements

### Requirement 1: IBD-Style HLC Bars (Bold)

**User Story:** As a trader, I want bold IBD-style HLC bars displayed on the chart, so that I can clearly read price action in the traditional IBD format without needing a separate candle indicator.

#### Acceptance Criteria

1. THE Indicator SHALL render each bar as an HLC bar consisting of a vertical line from the high to the low and a horizontal close tick on the right side, with no open tick displayed
2. WHEN the current close is greater than or equal to the prior close, THE Indicator SHALL color the HLC_Bar black
3. WHEN the current close is less than the prior close, THE Indicator SHALL color the HLC_Bar red
4. IF no prior close is available (first bar on the chart), THEN THE Indicator SHALL color the HLC_Bar black
5. THE Indicator SHALL render the HLC_Bar with a default line width of 3
6. THE Indicator SHALL allow the user to configure the bar line width via an input field with a minimum value of 2 and a maximum value of 10
7. THE Indicator SHALL hide the default chart candles by rendering in overlay mode on the main price chart

### Requirement 2: Moving Averages

**User Story:** As a trader, I want key moving averages displayed on the chart, so that I can identify support, resistance, and trend direction using IBD methodology.

#### Acceptance Criteria

1. THE Indicator SHALL plot a simple moving average of the closing price using a default period of 20 days, displayed in orange with a line width of 2
2. THE Indicator SHALL plot a simple moving average of the closing price using a default period of 50 days, displayed in red with a line width of 2
3. THE Indicator SHALL plot a simple moving average of the closing price using a default period of 200 days, displayed in blue with a line width of 2
4. THE Indicator SHALL allow the user to configure each moving average period via input fields with a minimum value of 1 and a maximum value of 500
5. IF the chart contains fewer bars than a configured moving average period, THEN THE Indicator SHALL begin plotting that moving average only from the bar where sufficient data becomes available

### Requirement 3: Volume Bars with Price-Action Coloring

**User Story:** As a trader, I want volume bars colored to match price action displayed in a separate pane, so that I can assess demand and supply without using a second indicator slot.

#### Acceptance Criteria

1. THE Indicator SHALL render volume bars in a separate pane below the price chart, where each bar's height represents the symbol's volume for that period
2. WHEN the current close is greater than or equal to the prior close, THE Indicator SHALL color the volume bar using the user-configured up color (default: black)
3. WHEN the current close is less than the prior close, THE Indicator SHALL color the volume bar using the user-configured down color (default: red)
4. IF the current bar is the first available bar (no prior close exists), THEN THE Indicator SHALL treat the bar as an up bar and apply the up color
5. THE Indicator SHALL plot a simple moving average of volume as a line overlaid on the volume bars, using the user-configured moving average period
6. THE Indicator SHALL allow the user to configure the volume moving average period via an input field with a default value of 50 and a minimum value of 1

### Requirement 4: Relative Strength Line

**User Story:** As a trader, I want a Relative Strength line plotted on the chart comparing my stock to a benchmark index, so that I can evaluate whether the stock is outperforming or underperforming the market.

#### Acceptance Criteria

1. THE Indicator SHALL calculate the RS_Line by dividing the stock closing price by the Benchmark_Index closing price on each bar
2. THE Indicator SHALL normalize the RS_Line so that its most recent value aligns with the stock's most recent closing price, scaling all prior RS_Line values proportionally to fit within the visible price chart range
3. THE Indicator SHALL plot the RS_Line as a continuous line in a user-configurable color with a default value of green, rendered behind the price bars
4. THE Indicator SHALL allow the user to configure the Benchmark_Index ticker symbol via an input field with a default value of "SPY"
5. IF the Benchmark_Index ticker symbol returns no data (request.security returns na for all bars), THEN THE Indicator SHALL display a warning label on the chart indicating the benchmark is unavailable and suppress the RS_Line plot
6. IF the Benchmark_Index data contains intermittent na values on individual bars, THEN THE Indicator SHALL carry forward the last valid RS_Line value to maintain line continuity

### Requirement 5: RS New High Indicator

**User Story:** As a trader, I want a visual marker when the RS line makes a new 52-week high, so that I can identify stocks showing leadership relative strength ahead of price breakouts.

#### Acceptance Criteria

1. WHEN the RS_Line value on the current bar strictly exceeds the highest RS_Line value over the previous 252 trading days (excluding the current bar), THE Indicator SHALL plot an RS_New_High_Dot as a blue circle below the price bar
2. THE Indicator SHALL plot the RS_New_High_Dot at a fixed offset below the bar's low using shape.circle with size.tiny so it does not obscure the price bar
3. THE Indicator SHALL allow the user to configure the lookback period for the RS new high calculation via an input field with a default of 252 days and a minimum value of 20
4. WHEN the RS_Line makes consecutive new highs on adjacent bars, THE Indicator SHALL plot an RS_New_High_Dot on each qualifying bar independently

### Requirement 6: Price Consolidation Pattern Detection

**User Story:** As a trader, I want the indicator to detect flat base and cup-with-handle consolidation patterns, so that I can identify potential breakout setups per IBD methodology.

#### Acceptance Criteria

1. WHEN the highest close minus the lowest close over a rolling window is within 15% of the highest close AND the window spans between 25 and 65 trading days, THE Consolidation_Detector SHALL identify a Flat_Base pattern
2. WHEN a Flat_Base is detected, THE Indicator SHALL highlight the consolidation range with a shaded background region spanning from the pattern start bar to the current bar, bounded vertically by the highest close and lowest close of the window
3. WHEN a price decline from a left-side high forms a rounded trough lasting at least 30 trading days AND the cup depth does not exceed 33% from the left-side high AND a subsequent handle forms that retraces no more than 12% from the handle high and lasts between 5 and 25 trading days, THE Consolidation_Detector SHALL identify a Cup_With_Handle pattern
4. WHEN a Flat_Base pattern is detected, THE Indicator SHALL plot the Pivot_Point as a horizontal dashed line at the highest close within the consolidation range
5. WHEN a Cup_With_Handle pattern is detected, THE Indicator SHALL plot the Pivot_Point as a horizontal dashed line at the highest price of the handle
6. THE Indicator SHALL allow the user to enable or disable pattern detection via an input toggle
7. IF pattern detection is enabled and no consolidation pattern meets the defined criteria over the most recent 65 trading days, THEN THE Indicator SHALL display no pattern markings on the chart

### Requirement 7: Key Price Levels

**User Story:** As a trader, I want the 52-week high and pivot point levels displayed on the chart, so that I can identify resistance levels and optimal buy points.

#### Acceptance Criteria

1. THE Indicator SHALL plot the Fifty_Two_Week_High as a horizontal line at the highest close over the trailing 252 trading days; IF fewer than 252 bars are available, THE Indicator SHALL use all available bars
2. THE Indicator SHALL display the Fifty_Two_Week_High line in purple with a dashed style, visually distinguishable from the existing MA lines
3. THE Indicator SHALL allow the user to enable or disable the 52-week high line via an input toggle (default: enabled)
4. WHEN the current close exceeds the Fifty_Two_Week_High, THE Indicator SHALL update the line to the new high on the next bar
5. WHEN a consolidation pattern Pivot_Point is active, THE Indicator SHALL display the pivot level as a separate horizontal line distinct from the 52-week high line
6. WHEN the 52-week high toggle is set to false, THE Indicator SHALL hide both the 52-week high line and its label from the chart

### Requirement 8: Single Indicator Consolidation

**User Story:** As a free-tier TradingView user, I want all IBD analysis tools combined into one indicator, so that I can use my second indicator slot for another tool.

#### Acceptance Criteria

1. THE Indicator SHALL operate as a single PineScript v6 indicator declaration with overlay=true
2. THE Indicator SHALL use a separate pane (via a secondary plot) only for volume bars, keeping all other visuals on the price overlay
3. THE Indicator SHALL remain within PineScript compilation limits: no more than 500 local variables per function scope, no more than 500 plot calls, and total script size under the compiler maximum
4. THE Indicator SHALL use no more than one request.security call for the Benchmark_Index data retrieval
5. THE Indicator SHALL provide input groups to organize settings into logical categories: "Price Bars", "Moving Averages", "Volume", "Relative Strength", "Patterns", and "Price Levels"
6. THE Indicator SHALL consolidate all components (HLC bars, moving averages, volume bars, RS line, RS new high dots, pattern detection, and key price levels) into this single indicator declaration

### Requirement 9: PineScript v6 Compatibility

**User Story:** As a developer, I want the indicator to be fully compatible with PineScript v6, so that it compiles and runs without errors on TradingView.

#### Acceptance Criteria

1. THE Indicator SHALL use the //@version=6 declaration as the first line of the script
2. THE Indicator SHALL use only PineScript v6 compatible functions and syntax, avoiding any functions removed or renamed in the v5-to-v6 migration (e.g., using `indicator()` instead of `study()`, `request.security()` instead of `security()`, `ta.*` namespaced functions instead of legacy function names)
3. THE Indicator SHALL compile with zero errors and zero warnings in the TradingView PineScript editor console
4. IF a PineScript v6 function is deprecated or unavailable, THEN THE Indicator SHALL use the replacement function documented in the official TradingView PineScript v6 migration guide
5. THE Indicator SHALL execute on a chart without producing runtime errors for any valid stock or ETF ticker with at least 252 bars of historical data available

### Requirement 10: User-Configurable Display Options

**User Story:** As a trader, I want to toggle individual components on and off, so that I can customize the chart view to my current analysis needs without indicator clutter.

#### Acceptance Criteria

1. THE Indicator SHALL provide a separate boolean input toggle for each of the following components: HLC bars, 20-period moving average, 50-period moving average, 200-period moving average, volume pane, RS line, RS new high dots, pattern detection, and 52-week high line
2. WHEN a component toggle is set to false, THE Indicator SHALL hide all visual elements associated with that component, including plot lines, shapes, labels, background fills, and table cells, so that no visual trace of the disabled component remains on the chart
3. THE Indicator SHALL default all component toggles to true (enabled)
4. WHEN a component toggle is set to false, THE Indicator SHALL continue to render all other enabled components without any change to their position, color, or scale

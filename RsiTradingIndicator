//@version=5
strategy('RSI Trading Bot', overlay=true)

// RSI threshold value and stop loss percentage
rsiThreshold = 30
stopLossPercentage = 1.5

// Calculate RSI
rsiLength = 14
rsiValue = ta.rsi(close, rsiLength)

// Initialize variables
var bool positionOpen = false
var float entryPrice = na
var float stopLossPrice = na

// Enter position when RSI crosses below threshold
if ta.crossunder(rsiValue, rsiThreshold)
    strategy.entry('Long', strategy.long)
    positionOpen := true
    entryPrice := close
    stopLossPrice := entryPrice * (1 - stopLossPercentage / 100)
    stopLossPrice

// Exit position on stop loss
if positionOpen and close < stopLossPrice
    strategy.close('Long')
    positionOpen := false
    entryPrice := na
    stopLossPrice := na
    stopLossPrice

// Plot entry and stop loss prices
plot(entryPrice, title='Entry Price', color=color.new(color.green, 0), linewidth=2)
plot(stopLossPrice, title='Stop Loss Price', color=color.new(color.red, 0), linewidth=2)


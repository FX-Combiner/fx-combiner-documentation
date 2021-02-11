# FX-Combiner Documentation
> :warning: **Forex trading involves risk and FX combiner team is not responsible for any losses suffered due to the product. We
accept no liability for its use. This is a setup guide to help you test your strategy.**

## Contact Details
Telegram Community: t.me/fxcombiner

## Compatibilty
FX Combiner currently is compatible with MT4 only.

## How to use the FX combiner with indicators
Quickest manner to setup the FX combiner with minimal settings – steps highlighted in green
Section A. Setup the EA and indicators on MT4:
1. Click on File → Open Data Folder to access the folder where files need to be placed
2. Copy the ex4 file (Fxcombiner) latest version to the data folder/MQL4/Experts.
3. Copy your indicators to the data folder/ MQL4/Indicators.
4. Right click on indicators / experts in MT4 Navigator section and click refresh. You should be able to now see your
indicators and FX combiner under the indicators and experts section
5. Please note that only indicators with buy and sell buffers send signals for entry and exit. Therefore, only such
indicators can be used in FX Combiner
Section B. Steps to setup the FX Combiner:
1. Select TradeType as NormalTrade
2. Enter a LotSize
3. Enter your Take Profit (TP) and Stop Loss (SL) values using absolute values OR Average True Range (ATR):
a. For absolute values: Enter Absolute values using fields Take Profit and Stop Loss
b. For ATR values:
i. Enter PeriodATR (Number of bars for calculating average range – example: 14)
ii. ATR Take Profit: Multiplier value – example: 10. This value is multiplied by range calculated by
ATR. For example, user sets ATR TP to 10, PeriodATR to 14, last 14 bars have an average of 8
PIPS, your TP will be set to 8 * 10 = 80 Pips
iii. ATR Stop Loss: Multiplier value similar to ATR Take Profit
4. Enter Slippage: In case the bar moves too quickly, allows opening / closing trades within the entry point + -
slippage value
5. Enable Trailing Stop to trail the current price by n pips
a. Set UseTrailingStop to true
b. Enter a value in PutStopLossAfter in Pips. Once a trade hits this value in the winning direction, stop loss
will be placed / modified on the trade. For a tight trail, enter lower value – Example 15
c. Enter a value in TrailingStop in Pips. The stop loss placed in previous step will be placed at
PutStopLossAfter – TrailingStop value. Example 10
d. Enter a value in TrailingStep in Pips. The stop loss placed earlier will be moved everytime the price
moves in the winning direction by this value. Example 1
e. Example: Using the above values and entering a buy trade, if a trade hits 15 pips above price, it will
move the SL to 5 pips (15-10) above entry price. Every time the price moves up, the SL will be moved by
1 pip. However if the price moves down, the trade will close at SL and make you a profit. Useful for
catching large price movements instead of closing at a fixed TP.
6. Enable Break Even settings to exit trades that momentarily going in your favor before reversing. This allows
exiting such trades without making a loss
a. Settings similar to TrailingStop and use the same logic. However, the SL is not moved every time the
price moves. For example, setting BreakEvenAfter to 8 and BreakEvenPips to 5 in a buy trade, will set a
SL on the trade at 5 Pips above entry price as soon as the price has hit 8 pips above entry price.
7. Enable Hedging setting (Applies only if trade type is set to Hedging)
a. Coming Soon
8. Enable Risk Management
a. Coming Soon
9. Close Trades on weekend
a. Coming Soon
10. IndicatorEntrySetting: Used to define how many indicators need to give you a signal in order to enter or exit a
trade.
a. How many confirmation a signal Entry. Example: If using 2 indicators with FX combiner and you want to
enter a trade when both indicators print a signal, enter 2 in this box.
b. How many confirmation a signal Exit: Example: If using 2 indicators with FX combiner and you want to
exit a trade when both indicators print a signal in the opposite direction of the entered trade, enter 2 in
this box.
11. Indicator1EntrySetting: Used to define the settings for your first indicator used to enter trades.
a. Set Indicator1-Enable to True
b. Indicator1 – File Name: Enter the exact file name of the indicator that you wish to use without the file
extension. Example: ‘Candle_Pips_Alerter’ (Without the ‘ symbols). These were indicators copied in
section A. of this guide
c. Indicator1 – Buy Buffer: default values – 0. Check your indicator for more information on what buffers
are being returned by it
d. Indicator1 – Sell Buffer: default values – 1. Check your indicator for more information on what buffers
are being returned by it
e. To check the buffer values in the indicator: Follow the below instructions:
i. Drag an indicator to a chart
ii. Go to Colors tab on the indicator configuration window
iii. Check the # column for the numeric values. Enter these values in the buffers section of the
indicator setting
iv. In case of more than 2 values, pick the ones that correspond to the signal colors printed on the
chart
f. Indicator1 – Bar0 or Intrabar: Set this to True if you wish to enter a trade as soon as the signal is given by
an indicator
g. Indicator1 – Bar1: Set to true to enter a trade - 1 bar after the signal was given by the indicator
h. Indicator1 – Bar2: Set to true to enter a trade - 2 bars after the signal was given by the indicator
i. Indicator1 – Bar3 – 4: Same as above but determines which bar will be used for entering a trade
j. * Setting multiple bars to true will initiate trades at the first qualifying bar
12. Inidicator2 – 5 Entry Settings: Similar settings to configure if you are using more than 1 indicator with FX
combiner. Note that you may enter settings in all 5 indicators and enable them, however entry to a trade will
depend on the IndicatorEntrySetting section.
13. Indicator1 – 5 Exit settings: Similar settings to configure indicators used for exiting trades
14. Note that if you do not wish to use an indicator for exiting trades and rely on TP / SL to exit, simple set all 5 exit
indicator settings to False and set the number of confirmation signals in IndicatorEntrySetting to 1
15. AlertSetting: Used to enable alerts
16. UseNewsFilter: Used to disabling trading during posted news events

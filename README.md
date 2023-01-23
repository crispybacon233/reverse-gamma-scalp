# reverse-gamma-scalp
This is a paper trading bot that makes adjustments to the open position based on net delta between the short option and the underlying shares. The goal is to algorithmically
adjust the position when certain criteria are met. Basically, it's a 
trading bot for [reverse gamma scalping](https://www.tastylive.com/news-insights/the-dish-on-gamma-scalping). It will sell the call of your choosing and automatically buy/sell
shares of the underlying to maintain delta neutrality (or whatever you set the target_net_delta to).
<br></br>
This project uses TD Ameirtrade's API and Alpaca Trading API. New sign-ups for TD Ameritrade's API are no longer available, but if you already have an existing key,
this project should work for you.
The following packages were used:
<li>pandas</li>
<li>requests</li>
<li>json</li>
<li>time</li>
<li>datetime</li>

<br></br>
To use this bot, you need to create an [Alpaca](https://alpaca.markets/) account which is free. It will generate a key ID and secret key on your main dashboard.
Create a config.py file in the main folder with the following lines:
<li>ALPACA_KEY_ID = 'youralpacakeyid'</li>
<li>ALPACA_SECRET_KEY = 'youralpacasecretkey'</li>
<li>TDA_ID = 'yourTDAid'</li>
<br></br>
Once the config is setup, set the ticker to whatever you want, but make sure the expiration date and strike price is a valid, existing contract. Also, pay attention
to the final number in the exp_date variable. That is the number of days remaining until expiration. If that number is not completely accurate
, TD Ameritrade will throw an error. The time_interval is how often (in seconds) the program will check the position and make adjustments accordingly. The bot automatically
closes all position three minutes before market close. 
<br></br>

![Untitled](https://user-images.githubusercontent.com/89396780/214153253-c1586e40-fa63-494f-8f04-3f04aecc38d5.png)

Profit is made when the stock does not fluctuate too much during the day. Time decay is working to your advantage. But if the stock does make large moves, the bot will automatically buy/sell shares to maintain the target net delta. This will minimize losses. 

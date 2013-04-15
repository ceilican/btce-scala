btce-scala
==========

Scala Client for BTC-E Trade and Market Data APIs. BTC-E is the Cryptocurrencies(Bitcoin/Litecoin/Namecoin/...) Broker

Dependencies
------------

Client depends on Lift-JSON library (a part of the Lift framework, but could be used separately). Add following SBT dependency:

`"net.liftweb" % "lift-json_2.10" % "2.5-M4"`

or download and put jar to appropriate folder etc.

How to Use the Client
---------------------

To set credentials, create own implementation of ClientCredentials trait:

    object MyClientCredentials extends ClientCredentials {
        val Key = "my key"
        val Secret = "my secret"
    }

By default, WS library from Play framework is used for HTTP requests. To replace 
it, implement abstract functions *getRequest* (for Market Data API Client), *signedPostRequest* (for Trade API Client), *releaseConnections* (if needed) from HttpApiClient trait
and make own trade API and market data API implementations as:

`class MyTradeApiClient(credentials: ClientCredentials) extends TradeApiClient(credentials) with MyHttpApiClient`

and

`class MyMarketDataApiClient extends MarketDataApiClient with MyHttpApiClient`



Weak points
-----------

* Current version extracts only funds information from *getInfo* method results
* Only WS HTTP library (from Play framework) supported now. But it's easy to work with an another

Donations
---------

Please, support my work:

BTC: 1NJPJf1dqkEXwfBCHBLvLoQBMd6TG7gdLy

LTC: 4G5g5Ht6rSGz3bZ6NXua7rSgBkRboBVygi


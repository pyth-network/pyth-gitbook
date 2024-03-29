# Product Metadata

Product accounts store metadata about a product. This metadata is represented as a set of reference attributes, stored as a list of text key/value pairs but not all products share the same account structure.

Every product has `product_account`, `symbol`, `asset_type`, `quote_currency`, `base` and `price_account`. However, the remaining fields of a product account will depend on its `asset_type.`

**Equity**

As a rule, all products with `asset_type` = Equity will follow the below Product Account structure:

```
product_account... Solana Account
  symbol.......... AssetType.Country.BaseCurrency/QuoteCurrency
  asset_type...... AssetType
  quote_currency.. QuoteCurrency
  description..... Description
  base............ BaseCurrency
  country......... Country
  cms_symbol...... NYSESymbol
  cqs_symbol...... SIPSSymbol
  nasdaq_symbol... ComstockSymbol
  price_account... Solana Account
```

`symbol`: AssetType.Country.BaseCurrency/QuoteCurrency where the `base`: BaseCurrency is, in order of availability:&#x20;

1. `cms_symbol`: NYSESymbol&#x20;
2. `cqs_symbol`: SIPSSymbol
3. `nasdaq_symbol`: ComstockSymbol

Here is a snapshot of the Apple product account:

```
product_account .. G89jkM5wFLpmnbvRbeePUumxsJyzoXaRfgBVjyx2CPzQ
  symbol.......... Equity.US.AAPL/USD
  asset_type...... Equity
  quote_currency.. USD
  description..... APPLE INC
  base............ AAPL
  country......... US
  cms_symbol...... AAPL
  cqs_symbol...... AAPL
  nasdaq_symbol... AAPL
  price_account... CqFJLrT4rSpA46RQkVYWn8tdBDuQ7p7RXcp6Um76oaph
```

**Crypto**

As a rule, all products with `asset_type` = Crypto will follow the below Product Account structure:

```
product_account .. Solana Account
  symbol.......... AssetType.BaseCurrency/QuoteCurrency
  asset_type...... AssetType
  quote_currency.. QuoteCurrency
  description..... Description
  generic_symbol.. JLQDSymbol
  base............ BaseCurrency
  price_account .. Solana Account
```

Here is a snapshot of the Luna product account:

```
product_account .. 25tCF4ChvZyNP67xwLuYoAKuoAcSV13xrmP9YTwSPnZY
  symbol.......... Crypto.LUNA/USD
  asset_type...... Crypto
  quote_currency.. USD
  description..... LUNA/USD
  generic_symbol.. LUNAUSD
  base............ LUNA
  price_account .. 8PugCXTAHLM9kfLSQWe2njE5pzAgUdpPk3Nx5zSm7BD3
```

**Foreign Currency & Metal**

Lastly, are Foreign Currencies (FX) and Metal assets. Those 2 `asset_type` share a common product account structure that follows the below template:

```
product_account .. Solana Account
  symbol.......... AssetType.BaseCurrency/QuoteCurrency
  asset_type...... AssetType  
  quote_currency.. QuoteCurrency
  description..... Description  
  generic_symbol.. JLQDSymbol  
  base............ BaseCurrency
  tenor........... Maturity  
  price_account .. Solana Account
```

Here is a snapshot of the Japanese Yen product account:

```
product_account .. CiTV5gD8G53M1EQdo32jy5riYRU8fMFSVWC5wJj3vjcr
  symbol.......... FX.USD/JPY
  asset_type...... FX
  quote_currency.. JPY
  description..... USD/JPY
  generic_symbol.. USDJPY
  base............ USD
  tenor........... Spot
  price_account .. 3CVi3EEprs1zeKhv5kw9EpRDv1hNfvpunQ98gex27Prd
```

**Best  Practices**

The users should not rely on the symbol name being unchanging or parse data out of the symbol.

Instead, programs should always use the different attributes to identify the product you are interested in. You have to ensure that anything which is used to compose the symbol is made available as a stand-alone attribute.

**Caveats**

We’re limited to 464 bytes to store the attribute dictionary in v2 (the product account is 512 bytes and 48 are used for other fields). This has to hold all the keys and values, plus field separators. There is no data compression or abbreviation.

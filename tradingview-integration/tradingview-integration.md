---
description: Integrate Pyth price feeds on your application user interface with the TradingView widget
---

The TradingView integration is a web-based widget that allows users to view Pyth prices on their own website. All Pyth prices made available through the TradingView integration are originating from [Pythnet](../pythnet-price-feeds/pythnet-price-feeds.md).

# Technical Integration

1. Add the following script(s) from [TradingView](https://www.tradingview.com/widget/advanced-chart/) to your website depending on your framework:

{% tabs %}
{% tab title="html" %}

```html
<!-- TradingView Widget BEGIN -->
<div class="tradingview-widget-container">
  <div id="tradingview"></div>
  <script
    type="text/javascript"
    src="https://s3.tradingview.com/tv.js"
  ></script>
  <script type="text/javascript">
    new TradingView.widget({
      autosize: true,
      symbol: "PYTH:BTCUSD",
      interval: "D",
      timezone: "Etc/UTC",
      theme: "light",
      style: "1",
      locale: "en",
      toolbar_bg: "#f1f3f6",
      enable_publishing: false,
      allow_symbol_change: true,
      container_id: "tradingview",
    });
  </script>
</div>
<!-- TradingView Widget END -->
```

{% endtab %}

{% tab title="React" %}

```jsx
// TradingViewWidget.jsx

import React, { useEffect, useRef } from "react";

let tvScriptLoadingPromise;

export default function TradingViewWidget() {
  const onLoadScriptRef = useRef();

  useEffect(() => {
    onLoadScriptRef.current = createWidget;

    if (!tvScriptLoadingPromise) {
      tvScriptLoadingPromise = new Promise((resolve) => {
        const script = document.createElement("script");
        script.id = "tradingview-widget-loading-script";
        script.src = "https://s3.tradingview.com/tv.js";
        script.type = "text/javascript";
        script.onload = resolve;

        document.head.appendChild(script);
      });
    }

    tvScriptLoadingPromise.then(
      () => onLoadScriptRef.current && onLoadScriptRef.current()
    );

    return () => (onLoadScriptRef.current = null);

    function createWidget() {
      if (document.getElementById("tradingview") && "TradingView" in window) {
        new window.TradingView.widget({
          autosize: true,
          symbol: "PYTH:BTCUSD",
          interval: "D",
          timezone: "Etc/UTC",
          theme: "light",
          style: "1",
          locale: "en",
          toolbar_bg: "#f1f3f6",
          enable_publishing: false,
          allow_symbol_change: true,
          container_id: "tradingview",
        });
      }
    }
  }, []);

  return (
    <div className="tradingview-widget-container">
      <div id="tradingview" />
    </div>
  );
}
```

{% endtab %}
{% endtabs %}

2. Replace the `symbol` parameter with the Pyth symbol you want to display. For example, to display the price of Ethereum, use `symbol: "PYTH:ETHUSD"`.

3. Replace the `interval` parameter with the time interval you want to display. For example, to display the price of Ethereum in 1-minute intervals, use `interval: "1"`. Possible resolutions are daily (D or 1D, 2D ... ), weekly (1W, 2W ...), monthly (1M, 2M...) and an intra-day resolution – minutes(1, 2 ...).

4. Replace the `timezone` parameter with the timezone you want to display. For example, to display the price of Ethereum in the Eastern Time Zone, use `timezone: "America/New_York"`.

5. Replace the `theme` parameter with the theme you want to display. For example, to display the price of Ethereum in dark mode, use `theme: "dark"`.

6. There is a fully working open-source example of the TradingView integration by one of Pyth's contributors [here](https://github.com/cctdaniel/pyth-tv-example). The example application is deployed [here](https://pyth-tv-example.vercel.app/).

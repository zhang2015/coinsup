<template>
    <div id="tv_chart_container" style="height: 100px;margin:auto"></div>
</template>

<script>
export default {
  name: "tv",
  data() {
    return {};
  },
  mounted() {
    var widget = (window.tvWidget = new TradingView.widget({
      fullscreen: true,
      width: "100%",
      symbol: 'ETH/BTC',
      interval: "D", //初始化显示的时间范围
      container_id: "tv_chart_container",
      datafeed: new Datafeeds.UDFCompatibleDatafeed(
        "http://api.exchange-data.coinsup.top/v1/trading-data",
        10000
      ),
      library_path: "../../../static/charting_library/",
      locale: "zh",
      autosize: true,
      timezone: "Etc/UTC",
      toolbar_bg: "#121c31",
      custom_css_url: "style/black.css",
      drawings_access: { type: "black", tools: [{ name: "Regression Trend" }] },
      disabled_features: [
        //禁用功能（隐藏图标按钮）数组
        "use_localstorage_for_settings"
      ],
      preset: "mobile",
      overrides: {
        "symbolWatermarkProperties.color": "rgba(0,0,0, 0)",
        "paneProperties.background": "#20334d",
        "paneProperties.vertGridProperties.color": "#344568",
        "paneProperties.horzGridProperties.color": "#344568",
        "paneProperties.crossHairProperties.color": "#58637a",
        "paneProperties.crossHairProperties.style": 2,
        "mainSeriesProperties.style": 9,
        "mainSeriesProperties.showCountdown": false,
        "scalesProperties.showSeriesLastValue": true,
        "mainSeriesProperties.visible": false,
        "mainSeriesProperties.showPriceLine": false,
        "mainSeriesProperties.priceLineWidth": 1,
        "mainSeriesProperties.lockScale": false,
        "mainSeriesProperties.minTick": "default",
        "mainSeriesProperties.extendedHours": false,
        volumePaneSize: "tiny",
        editorFontsList: [
          "Lato",
          "Arial",
          "Verdana",
          "Courier New",
          "Times New Roman"
        ],
        "paneProperties.topMargin": 5,
        "paneProperties.bottomMargin": 5,
        "paneProperties.leftAxisProperties.autoScale": true,
        "paneProperties.leftAxisProperties.autoScaleDisabled": false,
        "paneProperties.leftAxisProperties.percentage": false,
        "paneProperties.leftAxisProperties.percentageDisabled": false,
        "paneProperties.leftAxisProperties.log": false,
        "paneProperties.leftAxisProperties.logDisabled": false,
        "paneProperties.leftAxisProperties.alignLabels": true,
        // "paneProperties.legendProperties.showStudyArguments": true,
        "paneProperties.legendProperties.showStudyTitles": true,
        "paneProperties.legendProperties.showStudyValues": true,
        "paneProperties.legendProperties.showSeriesTitle": true,
        "paneProperties.legendProperties.showSeriesOHLC": true,
        "scalesProperties.showLeftScale": false,
        "scalesProperties.showRightScale": true,
        "scalesProperties.backgroundColor": "#20334d",
        "scalesProperties.lineColor": "#46587b",
        "scalesProperties.textColor": "#8f98ad",
        "scalesProperties.scaleSeriesOnly": false,
        "mainSeriesProperties.priceAxisProperties.autoScale": true,
        "mainSeriesProperties.priceAxisProperties.autoScaleDisabled": false,
        "mainSeriesProperties.priceAxisProperties.percentage": false,
        "mainSeriesProperties.priceAxisProperties.percentageDisabled": false,
        "mainSeriesProperties.priceAxisProperties.log": false,
        "mainSeriesProperties.priceAxisProperties.logDisabled": false,
        "mainSeriesProperties.candleStyle.upColor": "#3fcfb4",
        "mainSeriesProperties.candleStyle.downColor": "#fe4761",
        "mainSeriesProperties.candleStyle.drawWick": true,
        "mainSeriesProperties.candleStyle.drawBorder": true,
        "mainSeriesProperties.candleStyle.borderColor": "#3fcfb4",
        "mainSeriesProperties.candleStyle.borderUpColor": "#3fcfb4",
        "mainSeriesProperties.candleStyle.borderDownColor": "#fe4761",
        "mainSeriesProperties.candleStyle.wickColor": "#737375",
        "mainSeriesProperties.candleStyle.wickUpColor": "#3fcfb4",
        "mainSeriesProperties.candleStyle.wickDownColor": "#fe4761",
        "mainSeriesProperties.candleStyle.barColorsOnPrevClose": false,
        "mainSeriesProperties.hollowCandleStyle.upColor": "#3fcfb4",
        "mainSeriesProperties.hollowCandleStyle.downColor": "#fe4761",
        "mainSeriesProperties.hollowCandleStyle.drawWick": true,
        "mainSeriesProperties.hollowCandleStyle.drawBorder": true,
        "mainSeriesProperties.hollowCandleStyle.borderColor": "#3fcfb4",
        "mainSeriesProperties.hollowCandleStyle.borderUpColor": "#3fcfb4",
        "mainSeriesProperties.hollowCandleStyle.borderDownColor": "#fe4761",
        "mainSeriesProperties.hollowCandleStyle.wickColor": "#737375",
        "mainSeriesProperties.hollowCandleStyle.wickUpColor": "#3fcfb4",
        "mainSeriesProperties.hollowCandleStyle.wickDownColor": "#fe4761",
        "mainSeriesProperties.haStyle.upColor": "#3fcfb4",
        "mainSeriesProperties.haStyle.downColor": "#fe4761",
        "mainSeriesProperties.haStyle.drawWick": true,
        "mainSeriesProperties.haStyle.drawBorder": true,
        "mainSeriesProperties.haStyle.borderColor": "#3fcfb4",
        "mainSeriesProperties.haStyle.borderUpColor": "#3fcfb4",
        "mainSeriesProperties.haStyle.borderDownColor": "#fe4761",
        "mainSeriesProperties.haStyle.wickColor": "#737375",
        "mainSeriesProperties.haStyle.wickUpColor": "#3fcfb4",
        "mainSeriesProperties.haStyle.wickDownColor": "#fe4761",
        "mainSeriesProperties.haStyle.barColorsOnPrevClose": false,
        "mainSeriesProperties.barStyle.upColor": "#3fcfb4",
        "mainSeriesProperties.barStyle.downColor": "#fe4761",
        "mainSeriesProperties.barStyle.barColorsOnPrevClose": false,
        "mainSeriesProperties.barStyle.dontDrawOpen": false,
        "mainSeriesProperties.lineStyle.color": "#0cbef3",
        "mainSeriesProperties.lineStyle.linestyle": 0,
        "mainSeriesProperties.lineStyle.linewidth": 1,
        "mainSeriesProperties.lineStyle.priceSource": "close",
        "mainSeriesProperties.areaStyle.color1": "#0cbef3",
        "mainSeriesProperties.areaStyle.color2": "#0098c4",
        "mainSeriesProperties.areaStyle.linecolor": "#0cbef3",
        "mainSeriesProperties.areaStyle.linestyle": 0,
        "mainSeriesProperties.areaStyle.linewidth": 1,
        "mainSeriesProperties.areaStyle.priceSource": "close",
        "mainSeriesProperties.areaStyle.transparency": 80
      },
      studies_overrides: {
        //柱状颜色修改
        "volume.volume.color.0": "#F03869",
        "volume.volume.color.1": "#09BB07"
      }
    }));
  }
};
</script>
<style>
iframe {
  height: 350px !important;
}
</style>
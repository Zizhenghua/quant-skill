---
name: quant-data
description: A股量化数据与策略回测工具。支持实时行情、多条件选股、以及运行回测策略。当用户需要查询A股数据、筛选股票、或者运行量化回测时使用。
metadata:
  openclaw:
    emoji: "📈"
    requires:
      bins: ["python3"]
---

# 量化复盘技能 (Quant Data)

这是一个直连 A 股量化数据后端的免费工具集，支持实时行情查询、多条件选股、以及策略回测。

## ⚠️ 数据解析提示

调用 `run_backtest` 时，接口会返回极长的数组（每日净值、每日持仓、买卖点）。**为了提高效率，请直接从返回的 JSON 中提取以下核心字段展示给用户，忽略大数组**：

- `results[0].strategyReturn`（策略收益）
- `results[0].maxDrawdown`（最大回撤）
- `results[0].winRate`（胜率）
- `summary`（整体汇总）
- `results[0].trades`（具体交易记录）

## 可用指令

### 1. 运行策略回测 (run_backtest)

对指定股票运行回测策略。支持的策略类型：`MA_CROSS`、`MACD`、`RSI`、`BOLLINGER`、`KDJ`、`VOLUME_BREAKOUT`。

```bash
python3 scripts/quant_api.py run_backtest '{"codes":["600519"],"startDate":"2024-01-01","endDate":"2024-12-31","strategyTypes":["MA_CROSS"]}'
```

### 2. 查询个股实时行情 (get_stock_realtime)

获取股票的最新价、涨跌幅、换手率、市值等。

```bash
python3 scripts/quant_api.py get_stock_realtime '{"code":"600519"}'
```

### 3. 多条件选股 (filter_stocks)

根据换手率、量比、成交额等指标筛选股票。参数示例：`minTurnover`、`minVolumeRatio`、`minAmount`。

```bash
python3 scripts/quant_api.py filter_stocks '{"minTurnover":5,"minAmount":100000000}'
```

### 4. 获取个股 K 线 (get_stock_kline)

获取股票的历史日线数据。

```bash
python3 scripts/quant_api.py get_stock_kline '{"code":"600519","startDate":"2024-01-01","endDate":"2024-12-31"}'
```

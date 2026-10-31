---
name: quant-data
description: A股量化数据与回测工具。
metadata:
  openclaw:
    emoji: "📈"
    requires:
      bins: ["python3"]
---

# 量化复盘技能

## 可用指令

### 1. 运行回测
\`\`\`bash
python3 scripts/quant_api.py run_backtest '{"codes":["600519"],"startDate":"2024-01-01","endDate":"2024-12-31","strategyTypes":["MA_CROSS"]}'
\`\`\`

### 2. 查询行情
\`\`\`bash
python3 scripts/quant_api.py get_stock_realtime '{"code":"600519"}'
\`\`\`

### 3. 选股
\`\`\`bash
python3 scripts/quant_api.py filter_stocks '{"minTurnover":5,"minAmount":100000000}'
\`\`\`
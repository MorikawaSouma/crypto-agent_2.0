# Multi-Agent Crypto Trading System (AI-Powered)

这是一个基于大型语言模型 (LLM) 和多智能体架构 (Multi-Agent) 的加密货币量化交易与回测系统。

系统模拟了顶级投资者的思维模式（如巴菲特、索罗斯、达里欧、西蒙斯），结合实时市场数据、宏观经济数据、链上数据和市场情绪，提供深入的投资分析和交易决策。

## ✨ 主要功能

*   **多智能体协同架构**:
    *   **Warren Buffett Agent**: 关注价值投资、链上基本面和长期持有逻辑。
    *   **George Soros Agent**: 关注市场反射性、宏观趋势和资金流动。
    *   **Ray Dalio Agent**: 关注全天候策略、经济周期和风险平价。
    *   **Jim Simons Agent**: 关注量化指标、统计套利和技术形态。
    *   **Sentiment Agent**: 关注市场情绪（恐慌/贪婪指数）和舆情分析。
    *   **Master Agent**: 汇总各子智能体的观点，进行加权决策和风险控制。

*   **真实数据驱动**:
    *   **市场数据**: 集成 Binance API (通过 CCXT) 获取实时 K 线数据。
    *   **宏观数据**: 集成 Yahoo Finance & Stooq 获取 S&P 500, 美元指数 (DXY), 10年期美债收益率, VIX 恐慌指数。
    *   **情绪数据**: 集成 Alternative.me 获取加密货币恐慌与贪婪指数。
    *   **链上数据**: 集成 Blockchain.com 获取活跃地址数和交易量数据。

*   **强大的 LLM 集成**:
    *   支持 DeepSeek V3/R1 等先进大模型进行推理和决策生成。

*   **完整的回测引擎**:
    *   支持自定义时间范围的历史回测。
    *   生成详细的性能报告（收益率、夏普比率、最大回撤等）。
    *   可视化资金曲线和买卖点。

## 🛠️ 安装指南

1.  **克隆仓库**
    ```bash
    git clone https://github.com/yourusername/crypto-agent-system.git
    cd crypto-agent-system
    ```

2.  **创建虚拟环境 (推荐)**
    ```bash
    python -m venv venv
    # Windows
    .\venv\Scripts\activate
    # Linux/Mac
    source venv/bin/activate
    ```

3.  **安装依赖**
    ```bash
    pip install -r crypto_trading_system/requirements.txt
    ```

4.  **配置环境变量**
    复制 `.env.example` 为 `.env` 并填入你的 API Key：
    ```bash
    cp .env.example .env
    ```
    
    `.env` 文件内容示例:
    ```ini
    # DeepSeek API (必须)
    DEEPSEEK_API_KEY=sk-your-key-here
    
    # Binance API (可选，用于实盘数据，不填则使用公共接口)
    BINANCE_API_KEY=your-binance-key
    BINANCE_SECRET=your-binance-secret
    
    # 代理设置 (如果在国内无法直连 API)
    PROXY_URL=http://127.0.0.1:7890
    ```

## 🚀 使用方法

### 1. 运行实时市场分析
生成当前市场的投资分析报告和交易信号。

```bash
python -m crypto_trading_system.main
```
结果将输出在终端并保存为 `trading_report.csv`。

### 2. 运行多智能体回测
在历史数据上测试智能体系统的表现。

```bash
python -m crypto_trading_system.run_agent_backtest
```
*   **配置回测范围**: 修改 `config.py` 中的 `START_TIME` 和 `END_TIME`。
*   **查看结果**: 回测完成后会生成 `backtest_chart_*.png` (资金曲线图) 和 `backtest_results_*.csv`。

## 📂 项目结构

```
crypto_trading_system/
├── agents/                 # 智能体核心逻辑
│   ├── base_agent.py       # 智能体基类
│   ├── master_agent.py     # 主控智能体 (决策融合)
│   └── strategy_agents.py  # 策略智能体 (巴菲特、索罗斯等)
├── config.py               # 全局配置文件
├── data_loader.py          # 交易所数据获取 (CCXT)
├── real_data_provider.py   # 宏观/情绪/链上数据获取
├── feature_engineering.py  # 技术指标计算 (TA-Lib/Pandas-TA)
├── llm_client.py           # LLM API 客户端
├── backtest_engine.py      # 回测引擎核心
├── agent_backtest.py       # 智能体回测逻辑封装
├── main.py                 # 实盘分析入口
└── run_agent_backtest.py   # 回测入口
```

## ⚠️ 免责声明

本项目仅供教育和研究使用，不构成任何投资建议。加密货币市场波动巨大，使用自动化交易系统存在资金损失风险。请对自己负责。

## 📄 License

MIT License

# 🤖 AI Stock Analyzer Pro

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.53+-red.svg)](https://streamlit.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

**Een krachtige real-time stock market analyzer met AI-powered research capabilities**

[Features](#-features) • [Quick Start](#-quick-start) • [Demo](#-demo) • [Documentation](#-documentation) • [Contributing](#-contributing)

</div>

---

## ✨ Features

### 📊 Real-Time Market Data
- **Live Price Streaming** via WebSocket (US stocks, crypto)
- **Multi-Market Support**: NYSE, NASDAQ, Crypto (BTC, ETH, SOL)
- **Auto-Reconnect**: Robust connection management
- **Rate Limiting**: Built-in protection for all providers

### 📈 Advanced Technical Analysis
- **RSI** (Relative Strength Index)
- **MACD** (Moving Average Convergence Divergence)
- **Bollinger Bands**
- **SMA/EMA** (Simple & Exponential Moving Averages)
- **ATR** (Average True Range)
- **Trading Signals**: Automatic bullish/bearish/neutral detection

### 🤖 AI-Powered Research
- **OpenRouter Integration**: Access to multiple AI models
- **FREE Model**: Xiaomi Mimo v2 Flash (no cost!)
- **Premium Models**: Claude 3.5 Sonnet, GPT-4, Llama 3.1
- **Smart Tool Use**: Automatic price lookup, technical analysis
- **Chat Interface**: Natural language stock research

### 📉 Interactive Visualization
- **Multi-Timeframe Charts**: 1m, 5m, 15m, 1h, 4h, 1D
- **Plotly Charts**: Beautiful, interactive, zoomable
- **Real-time Updates**: Live price ticker
- **Custom Watchlists**: Track your favorite symbols

### 🔒 100% Free Tier Available
- **No Trading**: Data-only APIs (view prices, analyze, research)
- **Alpaca Paper Trading**: FREE real-time US stock data
- **Binance Public API**: FREE crypto data (no auth required)
- **OpenRouter FREE**: Xiaomi model included

## 🎥 Demo

### Dashboard
Real-time price tracking met technische indicatoren en trading signals.

### AI Research Assistant
Chat met de AI analyst om diepgaande marktanalyses te krijgen:
- "Analyseer AAPL technisch en geef me trading signals"
- "Wat is de huidige trend van BTC-USD met RSI en MACD?"
- "Vergelijk NVDA met AMD op basis van recente price action"

### Multi-Timeframe Analysis
Schakel tussen timeframes (1m tot 1D) voor verschillende trading strategieën.

---

## 🚀 Quick Start

### Prerequisites
- Python 3.12 of hoger
- Git
- OpenRouter API key (gratis model beschikbaar!)
- Alpaca Paper Trading keys (gratis!)

### Installation

**1️⃣ Clone de repository**

```bash
git clone https://github.com/wmostert76/ai-stock-analyzer.git
cd ai-stock-analyzer
```

### 2. Maak een virtual environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Linux/Mac
source venv/bin/activate
```

### 3. Installeer dependencies

```bash
pip install -r requirements.txt
```

### 4. Configureer API keys

Kopieer `.env.example` naar `.env`:

```bash
copy .env.example .env  # Windows
cp .env.example .env    # Linux/Mac
```

Bewerk `.env` en voeg je API keys toe:

```env
# OpenRouter API (Required voor AI research)
OPENROUTER_API_KEY=your_key_here

# Alpaca API (Gratis voor US stocks)
# Aanmelden: https://alpaca.markets
ALPACA_API_KEY=your_key_here
ALPACA_SECRET_KEY=your_secret_here

# Twelve Data (Optioneel voor EU stocks)
# Gratis tier: https://twelvedata.com
TWELVE_DATA_API_KEY=your_key_here

# Alpha Vantage (Optioneel voor fundamentals)
# Gratis tier: https://www.alphavantage.co
ALPHA_VANTAGE_API_KEY=your_key_here
```

### 5. Start de applicatie

```bash
streamlit run app.py
```

De app opent automatisch in je browser op `http://localhost:8501`

## API Keys Verkrijgen

### OpenRouter (Verplicht voor AI features)
1. Ga naar [OpenRouter](https://openrouter.ai/)
2. Maak een account aan
3. Genereer een API key
4. **Gratis model standaard:** De app gebruikt standaard het **Xiaomi Mimo v2 Flash** model (GRATIS!)

**Modellen beschikbaar:**
- **Xiaomi Mimo v2 Flash (GRATIS)** - Default model
- **Google Gemini Flash 1.5 (GRATIS)** - Snel en gratis
- **Llama 3.2 3B (GRATIS)** - Meta's gratis model
- Claude 3.5 Sonnet (betaald - beste voor research)
- GPT-4 Turbo (betaald)
- En nog veel meer!

### Alpaca (Gratis - US Stocks)
1. Ga naar [Alpaca Markets](https://alpaca.markets)
2. Maak een gratis account
3. Gebruik paper trading keys (gratis, onbeperkt)

### Binance (Gratis - Crypto)
Geen API key nodig voor publieke data! Werkt out-of-the-box.

### Twelve Data (Optioneel - EU Stocks)
1. Ga naar [Twelve Data](https://twelvedata.com)
2. Gratis tier: 800 API calls/dag
3. Genereer API key

## Gebruik

### Dashboard
- Selecteer een symbol uit de watchlist
- Bekijk real-time prijzen
- Analyseer technische indicatoren
- Bekijk trading signals

### AI Research
Stel vragen aan de AI analyst:

```
"Analyseer AAPL en geef me een technische analyse"
"Wat is de trend van BTC-USD?"
"Vergelijk NVDA met AMD op basis van recente performance"
```

De agent gebruikt automatisch de juiste tools om:
- Actuele prijzen op te halen
- Technische indicatoren te berekenen
- Nieuws te zoeken (coming soon)
- Fundamentals op te halen (coming soon)

### Watchlist Beheer
- Voeg symbolen toe via de sidebar
- Verwijder symbolen door ze uit de lijst te selecteren
- Ondersteunde formats:
  - US stocks: `AAPL`, `MSFT`, `TSLA`
  - EU stocks: `ASML.AS`, `SHELL.AS`
  - Crypto: `BTC-USD`, `ETH-USD`

## Technische Details

### Architectuur

```
├── app.py                      # Streamlit entry point
├── core/
│   ├── data_manager.py         # Data orchestration
│   └── state_manager.py        # Streamlit state
├── data_sources/
│   ├── alpaca_provider.py      # US stocks
│   ├── binance_provider.py     # Crypto
│   └── base.py                 # Provider interface
├── analysis/
│   └── technical_indicators.py # TA calculations
├── llm_agent/
│   ├── agent_core.py           # Research agent
│   ├── openrouter_provider.py  # OpenRouter API
│   └── tools/                  # Agent tools
└── config/
    ├── settings.py             # Configuration
    └── symbols.py              # Watchlists
```

### Data Sources

| Markt | Provider | Kosten | WebSocket |
|-------|----------|--------|-----------|
| US Stocks | Alpaca | Gratis | ✅ |
| Crypto | Binance | Gratis | ✅ |
| EU Stocks | Twelve Data | Gratis tier | ✅ |

### Technische Indicatoren

- **RSI** (Relative Strength Index)
- **MACD** (Moving Average Convergence Divergence)
- **Bollinger Bands**
- **SMA** (Simple Moving Averages: 20, 50, 200)
- **EMA** (Exponential Moving Averages: 12, 26)
- **ATR** (Average True Range)

## Troubleshooting

### "Alpaca API keys not configured"
- Controleer of je API keys correct zijn in `.env`
- Herstart de applicatie

### "No data available"
- Controleer internetverbinding
- Verificeer dat het symbol bestaat
- Check API rate limits

### WebSocket disconnections
- Automatische reconnection is ingebouwd
- Check firewall settings voor WebSocket verbindingen

## Roadmap

- [x] Real-time prijzen (US, EU, Crypto)
- [x] Technische indicatoren
- [x] AI Research Agent
- [ ] News integration
- [ ] Fundamentals data
- [ ] Portfolio tracking
- [ ] Backtesting
- [ ] Alerts & notifications
- [ ] Multi-timeframe analysis

## Credits

Gebouwd met:
- [Streamlit](https://streamlit.io)
- [Alpaca](https://alpaca.markets)
- [Binance](https://www.binance.com)
- [OpenRouter](https://openrouter.ai)
- [pandas-ta](https://github.com/twopirllc/pandas-ta)

## 🤝 Contributing

Contributions are welcome! Hier is hoe je kunt bijdragen:

1. Fork de repository
2. Maak een feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit je changes (`git commit -m 'Add some AmazingFeature'`)
4. Push naar de branch (`git push origin feature/AmazingFeature`)
5. Open een Pull Request

### Development Setup

```bash
# Clone je fork
git clone https://github.com/your-username/ai-stock-analyzer.git
cd ai-stock-analyzer

# Maak virtual environment
python -m venv venv
source venv/Scripts/activate  # Windows Git Bash

# Installeer dependencies
pip install -r requirements.txt

# Run tests
python test_setup.py
```

### Ideas voor Contributions
- [ ] European stocks support (Twelve Data integration)
- [ ] Portfolio tracking functionality
- [ ] Backtesting framework
- [ ] More technical indicators
- [ ] News sentiment analysis
- [ ] Real-time alerts/notifications
- [ ] Mobile-responsive design improvements

## 📝 Licentie

MIT License - zie [LICENSE](LICENSE) file voor details.

## 🙏 Acknowledgments

- [Streamlit](https://streamlit.io) - Beautiful UI framework
- [Alpaca Markets](https://alpaca.markets) - Real-time stock data
- [Binance](https://www.binance.com) - Crypto market data
- [OpenRouter](https://openrouter.ai) - Multi-model AI access
- [pandas-ta](https://github.com/twopirllc/pandas-ta) - Technical analysis library

## 📧 Contact

Voor vragen, suggesties of bug reports:
- Open een [GitHub Issue](https://github.com/wmostert76/ai-stock-analyzer/issues)
- Start een [Discussion](https://github.com/wmostert76/ai-stock-analyzer/discussions)

---

<div align="center">

**⭐ Star dit project als je het handig vindt!**

Made with ❤️ by the AI Stock Analyzer community

</div>

# Stock Analyzer Pro 📈

Een geavanceerde real-time stock analyzer met AI-powered research capabilities.

## Features

- ✅ **Real-time prijzen** voor US stocks, Europese aandelen, en crypto
- ✅ **Technische indicatoren**: RSI, MACD, Bollinger Bands, Moving Averages
- ✅ **AI Research Agent** via OpenRouter (Claude, GPT-4, Llama, etc.)
- ✅ **WebSocket streaming** voor real-time data
- ✅ **Multi-market support**: NYSE, NASDAQ, AEX, DAX, Crypto
- ✅ **Portfolio tracking** (coming soon)

## Installatie

### 1. Clone de repository

```bash
cd stockanalyzer
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

## Licentie

MIT License - zie LICENSE file voor details.

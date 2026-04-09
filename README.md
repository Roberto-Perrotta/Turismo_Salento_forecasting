# Turismo in Salento: Analisi, Forecasting e Pricing Dinamico

## Descrizione

Progetto di Data Science applicato al settore turistico della **provincia di Lecce (Salento)**, 
sviluppato come caso studio reale con dati pubblici ufficiali.

L'obiettivo è dimostrare come strumenti di analisi dei dati e forecasting possano supportare 
decisioni concrete nel settore ricettivo: dalla previsione della domanda all'ottimizzazione 
del pricing.

---

## Struttura del progetto

```
turismo_salento/
│
├── data/
│   └── lecce_turismo_pulito.csv        # Dataset elaborato (fonte: Istat)
│
├── notebooks/
│   ├── 01_raccolta_dati.ipynb          # Caricamento e pulizia dati Istat
│   ├── 02_analisi_esplorativa.ipynb    # KPI, trend e confronti territoriali
│   ├── 03_forecasting.ipynb            # Previsione domanda con Prophet
│   ├── 04_insight_business.ipynb       # Raccomandazioni operative
│   └── 05_pricing_dinamico.ipynb       # Analisi pricing con dati Airbnb
│
└── README.md
```

---

## Fonti dati

| Dataset | Fonte | Periodo |
|---|---|---|
| Movimento clienti esercizi ricettivi | Istat | 2014–2024 |
| Annunci e prezzi Airbnb | InsideAirbnb (Napoli, proxy Sud Italia) | Settembre 2025 |

---

## Notebook

### 01 — Raccolta e pulizia dati
- Caricamento di 11 fogli annuali dal file Istat (2014–2024)
- Filtro sulla provincia di Lecce (92 comuni)
- Gestione valori mancanti e normalizzazione
- Output: `lecce_turismo_pulito.csv` (760 righe, 27 colonne)

### 02 — Analisi esplorativa
- Trend arrivi e presenze 2014–2024
- Composizione italiani vs stranieri
- Top 10 comuni per volume di arrivi
- Permanenza media per anno

**Insight principali:**
- 2024 anno record: **1.35 milioni di arrivi** (+57% vs 2014)
- Stranieri triplicati dal 2019: dal 25% al **35% degli arrivi**
- Lecce città e costa crescono in modo complementare

### 03 — Forecasting con Prophet
- Modello Facebook Prophet su serie storica annuale
- Gestione evento Covid 2020 come outlier strutturale
- Previsione 2025–2028 con intervallo di confidenza 90%

**Risultati:**

| Anno | Arrivi previsti | Crescita vs 2024 |
|---|---|---|
| 2025 | 1.497.008 | +10.7% |
| 2026 | 1.617.104 | +19.6% |
| 2027 | 1.737.200 | +28.5% |
| 2028 | 1.857.625 | +37.4% |

### 04 — Insight di business
- Analisi accelerazione componente straniera
- Confronto crescita Lecce città vs comuni costieri
- Raccomandazioni operative per strutture ricettive

### 05 — Pricing dinamico
- Analisi 9.752 annunci Airbnb (proxy mercato Sud Italia)
- Relazione prezzo / occupancy / revenue annuo
- Strategia pricing a 3 fasce stagionali

**Strategia consigliata per il Salento:**

| Stagione | Periodo | Prezzo consigliato | Occupancy attesa |
|---|---|---|---|
| Alta | Luglio–Agosto | €150–200/notte | ~55% |
| Media | Giugno, Settembre | €100–150/notte | ~72% |
| Bassa | Apr–Mag, Ott | €50–100/notte | ~84% |

---

## Tecnologie utilizzate

- **Python** — pandas, numpy, matplotlib, seaborn
- **Prophet** (Meta) — forecasting serie storiche
- **Jupyter / Google Colab** — sviluppo notebook
- **Dati:** CSV, XLSX

---

## Autore

**Roberto Perrotta**  
Laureando in Data Science | 20 anni di esperienza nel settore turistico  
[GitHub](https://github.com/Roberto-Perrotta)

---

## Note metodologiche

- I dati Istat coprono il periodo 2014–2024 con granularità annuale e comunale
- Il modello Prophet gestisce la discontinuità Covid 2020 come evento straordinario
- L'analisi pricing usa dati Airbnb di Napoli come proxy per il mercato extra-alberghiero del Sud Italia; la metodologia è direttamente applicabile al Salento
- Le previsioni al 2028 vanno lette con cautela: il trend post-Covid è eccezionalmente forte e potrebbe non mantenersi invariato

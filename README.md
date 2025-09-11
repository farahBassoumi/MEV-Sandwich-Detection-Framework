# Sandwich Attack Detection & Profit Analysis on Ethereum

## Overview

This repository contains a modular pipeline for detecting **MEV sandwich attacks** on the Ethereum blockchain and computing the associated **attacker profits**. It leverages **Blocknative mempool data** and **Infura API** for blockchain event extraction, combined with custom Python logic for **transaction decoding**, **token flow analysis**, and **profit computation**.

The goal is to provide a fully reproducible framework for **research and analysis of DeFi sandwich attacks**, enabling data scientists and blockchain analysts to reproduce, extend, or study attacker behavior.

---

## Features

* **Blocknative Data Extraction**: Scripts to download hourly mempool transaction slices (`.csv.gz`) from Blocknative archive.
* **Infura Integration**: Retrieve detailed Ethereum transaction receipts using the Infura API.
* **Preprocessing & Cleaning**: Safe parsing of logs, filtering Transfer events, and cleaning malformed hex values.
* **Token Decoding & Flow Analysis**: Detects intermediary transfers to accurately trace token input/output across complex multi-hop swaps.
* **Sandwich Attack Detection**: Identifies front-run → victim → back-run triplets based on transaction order, block number, and token flow.
* **Profit Computation**: Calculates attacker profit using exact token match and ratio-based methods, normalizing by token decimals.
* **Modular Pipeline**: Each step can be executed independently and is optimized for large datasets.

---

## Folder Structure

```
sandwich_attack_detection/
│
│
├── infura_data_extraction.sh         # a script to extract data from infura
├── blocknative_data_loading_scripts.py           # Merge and preprocess Blocknative CSV files
├── infura_data_preprocessing.py  # clean data and Extract token_in and token_out with intermediary checks
├── sandwich_detection_with_profit_analysis.py    # Detect sandwich attack triplets and analyse attackers' profits
├── profit_usd_extraction.py       # compute and extracts attackers profits in usd with accurate data using moralis api
│
├── requirements.txt            # Python dependencies
└── README.md
```

---

## Installation

1. Clone this repository:

```bash
git clone https://github.com/yourusername/sandwich_attack_detection.git
cd sandwich_attack_detection
```

2. Create a Python virtual environment:

```bash
python -m venv venv
source venv/bin/activate   # Linux / MacOS
venv\Scripts\activate      # Windows
```

3. Install dependencies:

```bash
pip install -r requirements.txt
```

4. Set your **Infura API Key** and **Moralis API Key** in the relevant Python scripts:

```python
API_KEY_INFURA = "YOUR_INFURA_KEY_HERE"
API_KEY_MORALIS = "YOUR_MORALIS_KEY_HERE"
```

---

## Data Sources

* **moralis API**: Provides historical token values in usd for a given block number.
* **Infura API**: Provides Ethereum block and transaction receipts for decoding events.

---

## Contributing

Contributions are welcome! You can:

* Add support for additional DEXs
* Improve profit estimation logic
* Optimize pipeline for larger datasets
* Create visualizations for detected sandwich attacks

Please open an issue or pull request for any improvements.

---

## Contact

For any questions, you can reach out at `bassoumiifarah@gmail.com`.


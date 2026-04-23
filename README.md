# Token Calculator

A small browser-based token pricing calculator that loads model metadata from `./models.json` and lets you estimate token usage and cost.

## Features

- Load models from local `models.json`
- Fallback to `https://openrouter.ai/api/v1/models` when local file loading is blocked
- Search models by partial `id`, name, canonical slug, or description
- Copy selected model pricing into editable inputs
- Live calculations for:
  - Result #1: `Tokens = TPM × Time × TOKENS_SCALE`
  - Result #2: `Charge Fee = (Tokens × Input_Price + Tokens / Context_Ratio × Output_Price) × PRICE_SCALE`
  - Result #3: `Charge after Discount = Charge Fee × Discount`
  - Converted total: `Charge Fee × Discount × Exchange Rate`

## Inputs

- **Input price ($)** and **Output price ($)** are scaled from the selected model pricing by `PRICE_SCALE`
- **Context Ratio** defaults to `50`
- **TPM (10K)** defaults to `1`
- **Time (m)** defaults to `60`
- **Exchange Rate** defaults to `7.0`
- **Discount** defaults to `0.99`

## Scaling constants

- `PRICE_SCALE = 1000000`
- `TOKENS_SCALE = 0.01`

## Usage

1. Open `index.html` in a browser.
2. Search for a model using the filter input.
3. Select a model to populate the pricing fields.
4. Adjust TPM, time, context ratio, discount, and exchange rate.
5. Read the calculated results live.

## Notes

If your browser blocks `fetch('./models.json')` from `file://`, either:

- serve the folder over HTTP, or
- click **Load local models.json** and upload the file manually

## Files

- `index.html` — app UI and calculator logic
- `models.json` — model data source

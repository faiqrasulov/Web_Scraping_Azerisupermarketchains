# Price tracking across three Azerbaijani supermarket chains

> Project from 2023, kept as it was written.

Scrapes product and price lists from Bazarstore, Bravo and Neptun, saves one dated Excel file per
chain, and combines a month of files into one comparison.

## How it fits together

| Notebook | Job |
|---|---|
| `Bazarstore_Selenium.ipynb`, `BazarStore_new.ipynb` | Bazarstore |
| `Bravo_Selenium.ipynb` | Bravo |
| `Neptun_Scrape.ipynb` | Neptun, with brand and pack size parsed out of the product name |
| `run_all_price_scripts.ipynb` | Runs the three scrapers on a schedule with papermill |
| `open_all_price_notebooks.ipynb` | Takes a chain, month and year and merges that month's files |

## Sample output

- `Qiymet_list/`: one price list per chain from 18 July 2023.
- `monthy_analysis/`: the merged June 2023 file per chain.

## Run it

```bash
pip install selenium beautifulsoup4 pandas numpy papermill tqdm psutil openpyxl
jupyter notebook run_all_price_scripts.ipynb
```

Set the output folder at the end of each scraper notebook first.

## Limits

- The selectors are from July 2023 and the three sites have changed since.
- The last saved run of `run_all_price_scripts.ipynb` ends in an error while converting a sale
  price to a number.
- Column names are in Azerbaijani (`qiymet` = price, `endirim` = discount).
- `Morse_code convert.ipynb` is an unrelated small exercise.

## Files

`About.txt` holds the original notes. The `.html` files are rendered copies of the notebooks.

# ElMundo News Scraper

Scrape [ElMundo news library](https://www.elmundo.es/elmundo/hemeroteca) to extract spanish news.

ElMundo library contains news from 2003 to the current date. For each day, the scraper will go to the morning,
afternoon, and night index pages and collect all the news URLs. It will then proceed to each news page and extract the
content. For each news the scraper store the following attributes:

- `source` is the source of the news. Set as default to "ElMundo".
- `title` is the title extracted from the news page.
- `url` is the URL from which the news was extracted
- `dct` which stands for "document creation time", is a date in the format `YYYY-MM-DD`.
- `text` is the text extracted from the news page.

The result of the scrape is a `.csv` file that will be placed on the `data/` folder at the root of the current
directory.

Follow the steps below to process the scraping on your machine.

---

## Environment

Start by creating and activating a virtual environment.

```shell
virtualenv venv --python=python3.8
source venv/bin/python activate
```

Install the project dependencies.

```shell
pip install -r requirements.txt
```

---

## Scrape

To scrape a range of dates one just needs to run the following command.

```shell
python -m src.scrape --start_date "2004-01-01" --end_date "2004-12-31" --output_file "news04.csv"
```

This script collects the news from the year 2004 and stores them in the file `data/news04.csv`. As far as the runtime is
concerned, you can expect about an hour for each year you scrape, and the resulting file to take about 40 MB of disk
space. 

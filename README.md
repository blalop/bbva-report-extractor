# BBVA reports extractor
[![Build Status](https://travis-ci.com/blalop/accountman.svg?branch=master)](https://travis-ci.com/blalop/accountman)
[![Checked with mypy](http://www.mypy-lang.org/static/mypy_badge.svg)](http://mypy-lang.org/)
[![Made with Python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)

Library + script to extract your bank account movements from the pdf reports that BBVA provides each month. Export it to csv or sqlite.

A [Grafana dashboard](grafana/bank_movements.json) is provided to visualize this data.

## Downloading the reports

In [bbva.es](https://bbva.es), login and go to Posición global > Cuentas y Tarjetas > Ficha. Then click Operaciones > Extracto mensual cuentas. Ready to go!

## Using the libray

You can either provide the file to be read or the raw string:

```python
from bbva2pandas.file_handler import read_report
with open(filename, 'rb') as f:
    dataframe = read_report(f)
```

```python
from bbva2pandas.report_parser import parse_report_content
dataframe = report_parser.parse_report_content('filecontent')
```

## Running the script

The provided script loads all the PDFs in the provided directory and generates a CSV/sqlite file
```
usage: bbva2pandas [-h] [--output_filename OUTPUT_FILENAME] directory {csv,sqlite}
bbva2pandas: error: the following arguments are required: directory, output_format
```

## Testing

Run

```bash
python3 -m unittest discover tests
```
# elastic-gdpr-scanner

Scan Elasticsearch instances to check for GDPR compliance.

**Disclamer: Vincent Maury or Elastic cannot be held responsible for the use of this script! Use it at your own risk**

## Getting Started

These instructions will get you a copy of the project up and running on your local machine.

## Running the scanner

### Prerequisites

This piece of python has no other pre-requisite than **Python 3**.
It should work on any platform (tested on Windows so far).
No need for additional library.

### Running the script

Just clone this repository and run the script.

```
git clone https://github.com/blookot/elastic-gdpr-scanner
python elastic-gdpr-scanner.py
```

The script has several options:
* `-h` will display help.
* `--target TARGET` to enter a specific target (single IP or IP range in CIDR format, eg 10.50.3.0/24). Defaults to localhost.
* `--port PORT` to specify the port where Elasticsearch is running. Defaults to 9200.
* `--regex REGEX` to add a specific regular expression to look for in the documents, like your username. Default list of regexes provided in the script.
* `--nb-threads NB_THREADS` to specify how many hosts you want to scan in parallel. Defaults to 10.
* `--socket-timeout TIMEOUT` to set the timeout for socket connect (open port testing), in seconds. Set it to 2 on the Internet, 0.5 in local networks. Defaults to 2.
* `--no-scan` if you only want to inventory Elasticsearch instances (without going into indices and running the regex matching). Defaults to False (do the scan).
* `--out OUT` to specify the name of the log file to output results. Defaults to `es-gdpr-report.csv`
* `--verbose` turns on verbose output in console. Defaults to False.

### Report

You can grab the `es-gdpr-report.csv` file generated by this script, as a report.
This file has a CSV format, because I love Microsoft Excel :-)

## Authors

* **Vincent Maury** - *Initial commit* - [blookot](https://github.com/blookot)

## License

This project is licensed under the Apache 2.0 License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Check [this website](https://ipsec.pl/data-protection/2012/european-personal-data-regexp-patterns.html) for further regexes
* Found [this repo](https://github.com/tvfischer/gdpr-data-patterns-detection) which is a great initiative, but sadly empty...
* Inspired by my old vulnerability scanner startup... :-)

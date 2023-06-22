# dizzy-datasets

Public datasets from [Dizzy](https://dizzy-dev.cibr.qcri.org) – a darkweb analytical search engine.

The following datasets are from our 10-month Dizzy deployment in 2021/2022. We're working with our IRB to decide which parts of the complete dataset are _fine_ to share, given that some domains host illicit content. As of now, we'll be releasing one or more smaller datasets with useful annotations.

In order to preserve the privacy of domain operators, we only share the MD5 hash of the domain name (including .onion) in hexademical format. For example, the hash of Facebook's v3 onion domain in Python is:

```python
>>> import hashlib
>>> hashlib.md5(b"facebookwkhpilnemxj7asaniu7vnjjbiltxjqhye3mhbshg7kx5tfyd.onion").hexdigest()
'5a59274ccdd9a8c5cbe969e971e92aa5'
```

This way you'll be able to know if you have the same domain names by comparing their MD5 hashes. This is the methodology used by [Ahmia](https://ahmia.fi/blacklist/) to share blacklisted onion domains.

Each dataset is a JSON file (i.e., lines of JSON strings) that is compressed using ZIP archive file format. Make sure to uncompress the file before parsing it.

## [domains-basic.json.zip](https://raw.githubusercontent.com/cibr-qcri/dizzy-datasets/main/domains-basic.json.zip)

This dataset contains basic information of 32,555 unique onion domains from our crawl. Each line in the dataset file is a JSON dump of a key/value object describing a domain, as follows:

| Key        | Value                                                                                         |
|------------|-----------------------------------------------------------------------------------------------|
| domain     | MD5 hexadecimal hash of the onion domain with `.onion` TLD                                    |
| is_v3      | True is the domain is hosted by a v3 onion service                                            |
| category   | Domain category: "socialmedia", "marketplace", "pornography", "crypto", "indexer", or "other" |
| is_illicit | True if domain hosts illict or illegal content (e.g., CSAM, drugs)                            |

## [btc-basic.json.zip](https://raw.githubusercontent.com/cibr-qcri/dizzy-datasets/main/btc-basic.json.zip)

This dataset contains basic information of 514,050 Bitcoin addresses from our crawl. Each line in the dataset file is a JSON dump of a key/value object describing a Bitcoin address, which domain contained, and whether the domain self-attribute the address (i.e., as a payment or donation address). Note that a Bitcoin address may be contained in multiple domains, and a domain may contain multiple addresses. Note that Bitcoin addresses found in webpages, while valid in terms of their format, may not be used in practice (i.e., they don't appear in any transaction on the blockchain).

| Key           | Value                                                                      |
|---------------|----------------------------------------------------------------------------|
| address       | Bitcoin address                                                            |
| domain        | MD5 hexadecimal hash of the onion domain with `.onion` TLD                 |
| is_v3         | True is the domain is hosted by a v3 onion service                         |
| path          | Webpage URL path where the address was found                               |
| is_attributed | True if domain self-attribute the address as a payment or donation address |

## [pages-basic.json.zip](https://raw.githubusercontent.com/cibr-qcri/dizzy-datasets/main/pages-basic.json.zip)

This dataset contains basic information of 20,779 unique webpages from our crawl. Each line in the dataset file is a JSON dump of a key/value object describing a crawled webpage. This is a small sample of the complete crawl (60m pages), where each webpage maps to exactly one domain that is unique across the dataset.

| Key      | Value                                                      |
|----------|------------------------------------------------------------|
| crawl_at | Unix timestamp when the page was crawled                   |
| domain   | MD5 hexadecimal hash of the onion domain with `.onion` TLD |
| is_v3    | True is the domain is hosted by a v3 onion service         |
| path     | URL path to the crawled webpage                            |

## Citation

If you use Dizzy or any of its datasets, please cite the following [publication](https://arxiv.org/abs/2209.07202):
```
@inproceedings{boshmaf2023dizzy,
  title={Dizzy: Large-Scale Crawling and Analysis of Onion Services},
  author={Boshmaf, Yazan and Perera, Isuranga and Kumarasinghe, Udesh and Liyanage, Sajitha and Al Jawaheri, Husam},
  booktitle={Proceedings of the 18th ACM International Conference on Availability, Reliability and Security},
  year={2023}
}
```

## Acknowledgment

We would like to thank [Pieter Hartel](https://www.tudelft.nl/en/staff/pieter.hartel/) for his advice on data sharing.

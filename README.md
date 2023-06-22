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

## [domains-basic.json](https://raw.githubusercontent.com/cibr-qcri/dizzy-datasets/main/domains-basic.json)

This dataset contains basic webpage information of 37,479 unique domains from our crawl. Each line in the dataset file is a JSON dump of a key/value object describing a webpage of a domain. There is exactly one page per domain with the following information:

| Key             | Value                                                                       |
|-----------------|-----------------------------------------------------------------------------|
| domain_md5      | MD5 hexadecimal hash of the onion domain (see above)                        |
| crawl_timestamp | Unix timestamp when the page was crawled                                    |
| onion_version   | Onion service version number (2 or 3)                                       |
| is_homepage     | True if the page is returned when visiting the domain at root path          |
| url_path        | The path used to crawl the page or its final redirection in the same domain |

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

# dizzy-datasets

Public datasets from [Dizzy](https://dizzy-dev.cibr.qcri.org) – a darkweb analytical search engine.

The following datasets are from our 10-month Dizzy deployment in 2021/2022. We're working with our IRB to decide which parts of the complete dataset are _fine_ to share, given that some domains host illicit content. As of now, we'll be releasing one or more smaller datasets with useful annotations.

In order to preserve the privacy of domain operators, we only share the MD5 hash of the domain name (excluding .onion) in hexademical format. For example, Facebook's onion domain is `facebookwkhpilnemxj7asaniu7vnjjbiltxjqhye3mhbshg7kx5tfyd` and its MD5 hash is `0e8b44ac0c467c56ab19c6636adabdfb`. This way you'll be able to know if you have the same domain by comparing its MD5 hashes.

## [domains-basic.json](https://raw.githubusercontent.com/cibr-qcri/dizzy-datasets/main/domains-basic.json)

This dataset contains basic domain information from our crawl.

| Field           | Description                                                                    |
|-----------------|--------------------------------------------------------------------------------|
| domain_md5      | MD5 hexadecimal hash of the onion domain                                       |
| crawl_timestamp | Unix timestamp when the page was crawled                                       |
| onion_version   | Onion service version number                                                   |
| is_homepage     | True if the page is returned when visiting the domain at root path             |
| url_path        | The path used to crawl the page or or its final redirection in the same domain |

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

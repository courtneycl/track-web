---
layout: page
title:  "Code and repositories"
---

## How *Track web security compliance* works

**Data**

*Track security web compliance* currently measures `.gc.ca` and `.canada.ca` subdomains that are publicly accessible over HTTP. These domains and subdomains are provided by the Digital Transformation Office within the Treasury Board of Canada Secretariat.

**Architecture**

There are three parts to this product: a domain scanner which scans a list of domains and analyses their behaviour (*tracker*), a Cosmos DB instance which hosts the results of the scan, and a web app that displays the results (*track-web*).

**Stack**

*tracker* is written for Python 3.5 and up.

*track-web* is a Flask app written for Python 3.6 and up.

## Repositories

There are two individual repositories that make up *Track web security compliance*.

**[tracker](https://github.com/cds-snc/tracker)**

This repository holds the domain scanning tool and produces the data that fills the table. The scanning tool measures the behaviour of four “endpoints” of every domain and subdomain: `http://`, `http://www`, `https://`, and `https://www`. Data from these endpoints is used to characterize the overall behaviour of a domain or subdomain. These measurements are performed using [domain-scan](https://github.com/18F/domain-scan), a Python-based open source tool maintained by the U.S. General Services Administration. Domain-scan is used to efficiently coordinate and parallelize [pshtt](https://github.com/dhs-ncats/pshtt), [sslyze](https://github.com/nabla-c0d3/sslyze), and other tools for large batch scans.

The [tracker](https://github.com/cds-snc/tracker) repository contains further documentation on:
* Input and output data definitions
* How domains and subdomains are matched to domain owners
* Basics for setting up lambda scanners for massively parallel scanning
* How to edit existing components or add new components to the scanning system
* How to deploy locally

**[track-web](https://github.com/cds-snc/track-web)**

This repository holds the Flask app. Track-web takes the output of the domain scanning tool and displays the results in tables and charts on *Track web security compliance*.

The [track-web](https://github.com/cds-snc/track-web) repository contains further documentation on:

* How to create additional web pages, styles, charts, and datatables
* How to add Google Analytics and track events (download and filter events are built-in)
* How to deploy locally

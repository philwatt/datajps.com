---
layout: post
title: Cooper Data Integration Workbench
date: '2019-05-28 12:34:26'
---

We use probabilistic and deterministic matching approaches which calculates a probability of a match between two similar records about a person, place or business. For example, is ‘John Smith’ the same as ‘Jon Smith’ when the records have a matching address. Probably – maybe 90%, say. What if here is a slight difference in address though – so the street name on one record is ‘Acacia Avenue’, but another record it’s ‘Acacia Street’? Probably yes again, but maybe 80% this time.

Some use cases require a very high degree of confidence in matching – and 90% is just not good enough. In this case ‘John Smith’ is not the same as ‘Jon Smith’. Others need a lower threshold – say 85%, while others can be very loose – say 75%.

We provide a simple interface to enable data scientists and data engineers to choose the probability thresholds on a case by case basis, so they can tune data linkage results.

## Minimum Viable Product

We have standardised processes to bring data together. Our MVP provides a simple web interface to set matching thresholds for two datasets and create an extract of data for a cohort that matches agreed selection criteria, following the [5 Safes Framework](http://www.abs.gov.au/ausstats/abs@.nsf/Latestproducts/1160.0Main%20Features4Aug%202017?opendocument&tabname=S).

The diagram below shows the high level process that the Cooper product follows for matching or linking data together. The red dots indicate the process controls matched to the 5 Safes Framework

<figure class="kg-card kg-image-card"><img src="https://www.lucidchart.com/publicSegments/view/0aa36009-ecda-4904-ae29-ba7f96f54bae/image.png" class="kg-image"></figure>

We will follow with an enhanced automated secure file transfer capability, alternative industry standard linkage keys and finally the ability to geo-standardise input data to improve match results. Availability for these four areas is shown in our [roadmap.](https://datajps.com/data-superconductor-roadmap/)

## Back to [our offers](https://datajps.com/data-superconductor-offers-and-mvp)

Note that **_Data SuperConductor_** and all the related content for it **_is_**  **_not real - including this page. It's just a hypothetical university project._**


---
title: Portfolio
layout: single
permalink: /portfolio/
toc: true
---

## Haystacker

A first-of-its-kind video forensics tool powered by machine learning and large language models

* [Press Release](https://www.washingtonpost.com/pr/2024/08/20/washington-posts-new-ai-tool-featured-axios/)
* [Example Haystcker Story](https://wapo.st/3BnR9nv) ([PDF](https://drive.google.com/file/d/1nPxiEzg6v6gm6KjuklUl8wqw7QkLozno/view?usp=drive_link))

### Description

Haystacker was fully conceived and developed by my Reporting Tools team at The Washington Post.

The core pitch to the newsroom was that large language models can help journalists find reporting insights within large corpuses of unstructured data. We turned that hunch into a tool that uses an LLM to perform automated object detection in video.

Haystacker consists of three components: a React/Typescript frontend for reporters to interact with, a Django API layer/database and a video processing pipeline written with Dagster.

### My contributions

* My largest contribution was the introduction of semantic text search into the application. During a multi-month process, I gathered consensus for consequential engineering decisions. This included:
  * Selecting the right embedding model
  * Deciding when and where to generate the embeddings
  * Designing the data models to hold the vector database
  * Refactoring our text search API to support substring, exact match and semantic search
* I designed the data flow and several functional components of the React application.
* I designed and implemented the cloud deployment for both the React application and the data pipeline.
* I created and tested a data recovery run book in the event of Haystacker data corruption.

## Mass Shootings

A live updating page of mass shootings in America powered by Dagster and Slack

* [Project page](https://wapo.st/3ONrS9u) ([PDF](https://drive.google.com/file/d/129wuEmHEXtXYV5rKSa_AsubFR0OI-fTK/view?usp=drive_link))

### Description

The Mass Shootings package was a collaboration between the Data and Graphics desks in the Washington Post newsroom and my Reporting Tools team. Our goal was to report on the record number of mass shootings in America in 2023. 

My team recognized that feeding a reader-facing page with live data represented a significant editorial responsibility. If the pipeline failed to run, or served incorrect data, it would be tantamount to publishing incorrect facts in a news article. So we aimed to engineer the most robust data pipeline possible using the Dagster framework.

### My Contributions

* My team elected to use the Dagster framework to set up and manage the data pipeline. I designed and implemented the cloud deployment strategy using a combination of AWS resources (RDS, ECS, etc.).
* I also implemented a novel-for-our-team GPRC server, which allowed both this and future Dagster pipelines to operate in isolated computing environments.
* Together with a member of the Data team, I worked to define a clear data dictionary and a methodology for how to calculate our results from a raw incoming data source. As a final check, I devised a “blind” verification process where both the Data team member and I would separately follow our agreed methodology and ensure the results matched up.
* I created a bespoke Slack integration that allowed non-technical journalists to run the data pipeline in the event of breaking news.

## Tiktok crowdsourcing

A GDPR-compliant data pipeline processing hundreds of user-submitted TikTok data dumps

* [Formstack page](https://thewashingtonpost.formstack.com/forms/help_investigate_tiktoks_algorithm)
* [Story](https://wapo.st/3ZLEiEU) ([PDF](https://drive.google.com/file/d/1SxvofFTCqUnFapP8sBviAVmB7fTniIOt/view?usp=drive_link))

### Description

The Washington Post newsroom had an ambitious idea: collect TikTok browsing data from hundreds of readers. Our team was enlisted to implement a GDPR-compliant data pipeline.

Our solution consisted of three stages for the data. First, a Formstack form for readers to submit their zip files. Second, a “clean room” AWS S3 bucket where submissions could be scanned for malware. Finally, a third S3 bucket for newsroom reporters to access the results. A pair of AWS EventBridge-triggered Lambdas would shuttle data through the stages.

As users were submitting personally identifying information, we needed to make sure our system would only collect the information needed to produce reporting. At the same time, any unnecessary data loss would shrink the sample size–a bad outcome for reporters looking to make useful observations. For us, this meant a delicate coordination of API calls, malware checks, file copying and cleanup tasks.

### My Contributions

* I worked with a colleague to design an idempotent logical flow for the data. Our data processing lambdas can be run at any hour, in any order, any number of times and still produce an identical logical outcome.
* I worked with a Formstack representative to clarify vagaries in their API documentation. This was in service of improving our GDPR guarantee.  
* During launch, I quickly responded to a lambda outage that presented the processing of new submissions.

## Fatal Force database

A Peabody award-winning database of fatal police shootings in America

* [Project page](https://www.washingtonpost.com/graphics/investigations/police-shootings-database/) ([PDF](https://drive.google.com/file/d/1gvC5EjnacW-3Smvo52-XYZWwPSI7VCNA/view?usp=drive_link))
* [Data repository](https://github.com/washingtonpost/data-police-shootings)

### Description

Fatal Force is a flagship project for The Washington Post. It is the nation’s most comprehensive database on police violence and is a critical resource for reporters and researchers both in and outside the organization.

The project consists of several components: a Postgres database, a graphics package, a GitHub repo where data is made public and a Django admin where researchers input new data.

Fatal Force was started in 2015 in the wake of the killing of Michael Brown. In that time, the underlying database and code had gathered so much tech debt, that it threatened to scuttle the entire project. My team was tasked with modernizing and setting the project on stable footing for the future.

### My Contributions

* I worked with partner journalists to redefine the fatal force dictionary, ditching fields that were no longer useful and introducing new categories of data for future reporting.  
* I translated data dictionary into refined guardrails for the Django admin and data models.
* I refactored the data publishing process to reduce export time by two-thirds.
* I designed and implemented the final “cutover” script to transition from version one to version two of the project with zero downtime.  

## Hong Kong, Blizzard, gamers and a fight waged on Reddit

A case study for analyzing the proliferation of content on Reddit

* [Case study](https://github.com/newshopper/hongkongmei)
* [Code](https://github.com/newshopper/hongkongmei)

### Description

While at Columbia J-School, I was especially drawn to reporting on social media trends. And it so happened, while I was taking a “Computational Journalism” class, that a major protest exploded on the social internet. 

I think the following writeup from [the case study](https://observablehq.com/@aaronbrezel/hong-kong-blizzard-gamers-and-a-fight-waged-on-reddit) linked above captures the moment well:

>On Oct. 6, 2019, Hong Kong-based professional Hearthstone player Ng "Blitzchung" Wai Chung, expressed solidarity with anti-government protestors on a live Esports tournament stream. The video was quickly removed by organizers. However, early the next morning, links to Blitzchung's statement began appearing in posts around various subcommunities on Reddit.
>
>Blizzard, Hearthstone's developer, announced the next day that they had suspended Blitzchung from competitive play for a year and would deduct his tournament winnings. Protest posts against the company quickly appeared and spread far throughout the Reddit ecosystem. The Blizzard/Hong Kong controversy dominated various large subreddits for several days and quickly evolved from simple text and links to elaborate memes.

Two colleagues and I pitched to our professor to cover this protest. To simulate the tight deadlines of a newsroom, we were given two weeks to produce a story.

What you see linked above is the result of our ability to balance time, methodology and other school responsibilities.

### My Contributions

* I worked with my colleagues to set reasonable goals for our tight deadline and to divvy up responsibilities.
* I developed the breadth-first-search algorithm that searched across Reddit for posts related to the protests.
* I produced the Observable notebook linked above that visualized the results of the algorithm.

## Memery

A 2020 Master’s thesis demonstrating the use of image clustering algorithms to uncover reporting leads

* [Design document](https://docs.google.com/document/d/10hyJtqQBjf-VJ6SHqbh5AR4TOJ4sgcQKg8IoeWAjQ_c/edit?usp=sharing)

### Description

My work at Columbia University studying social media culminated in a master’s thesis project called “Memery”: a prototype tool for tracking the provenance of memes across the internet.

My co-author and I were particularly interested in tracking meme formats as they traveled from fringe alt-right communities like 4Chan and Reddit on to mainstream platforms like Twitter. We believed that we could leverage recent advances in computer vision to help declutter the complex interchange between internet subcultures and platforms.

We managed to create a regularly updating tableau of emerging meme formats in far right internet communities. Our work was awarded the 2020 Brown/Tow Award for Excellence in Computational Journalism.

### My Contributions

* I interviewed several working journalists and internet researchers to understand how they track content around the internet
* I created a series of scrapers to collect image-based posts from 4Chan, Reddit and Twitter.
* I developed an algorithm to group similar images together based on the DBSCAN clustering method, pHashing, and a review of cutting edge academic literature on image classification.

## The Great GitHub Migration

Organizing a migration of hundreds of repositories from one GitHub organization to another

* [Migration runbook](https://docs.google.com/document/d/17uVxlBcWDIBovW4zO3sJJnWsBahHn0C5yBACTS4ZsUY/edit?usp=sharing)
* [GitHub onboarding documemtation](https://docs.google.com/document/d/1EXjS6-D6UP8UWE8CdEsxT1x_KDw5ssbK/edit?usp=sharing&ouid=103284334455247383215&rtpof=true&sd=true)

### Description

In late 2023, The Washington Post engineering department announced they were moving to a new GitHub organization. Thousands of code repositories from dozens of independent teams would need to migrate like wildebeests across the plains of Africa.

I was responsible for coordinating the transfer for my own team, Reporting Tools. But shortly into my assignment, I realized that the department-level migration plan left out an important constituency–the newsroom.

The links above are a snapshot of the documentation I created to communicate and coordinate the migration for both my own team and the newsroom.

### My Contributions

* I coordinated the transfer for my own team (see “Migration runbook” link). This included creating our repository roster, defining our team-specific migration steps, doling out migration responsibilities and of course, writing documentation to smooth out the process.
* I identified the lack of newsroom support and worked with the cybersecurity team to establish a new, longer migration deadline for the newsroom.
* I coordinated with the data desk editor to repeat the migration process for her team. This included me creating a script to migrate the repos automatically, saving reporters from a tedious and time-consuming manual process.
* I established a Slack channel where I would communicate migration updates and share documentation.
* I ran several onboarding sessions where I walked reporters through the process of joining the new GitHub organization.

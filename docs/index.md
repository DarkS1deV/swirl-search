---
layout: default
title: SWIRL Overview
nav_order: 1
permalink: "/"
---
<details markdown="block">
  <summary>
    Table of Contents
  </summary>
  {: .text-delta }
- TOC
{:toc}
</details>

# SWIRL Overview

## What is SWIRL AI Connect?

SWIRL AI Connect is infrastructure software, deployed in your own environment, that connects most any Generative AI/LLM to enterprise data platforms, applications and information services *without copying*, indexing and/or ingesting data. 

SWIRL's no-code approach requires minimal IT involvement, leveraging your existing systems. SWIRL can also use your AI/LLMs to summarize data, answer questions, generate charts from structured data sets - and much more - without moving your data, trusting a third party, or deploying an expensive new repository.

SWIRL provides the full benefit of AI - personalized, secure and real-time - without disrupting your current systems or security systems. 

## How does SWIRL Re-Ranking work?

SWIRL AI Connect is an AI-powered [metasearch engine](https://en.wikipedia.org/wiki/Metasearch_engine). SWIRL's unique Reader LLM, which can be use most any embeddings, re-ranks results from responding sources so the user doesn't have to. 

The re-ranking process is roughly the following:
* Vectorize the user's query (or parts of it)
* Send the text of the user's query and/or the vector, to each source requested (or default)
* Asynchronously gather the results from each source
* Normalize the results from each source using jsonpath (or xpath)
* Vectorize each result snippet (or parts of it)
* Re-rank the results by aggregating the similarity, frequency and position, and adjusting for other factors like length variation, freshness, etc 

The [Xethub study](https://about.xethub.com/blog/you-dont-need-a-vector-database) as [explained by Simson Garfinkel](https://www.linkedin.com/pulse/vector-databases-rag-simson-garfinkel-hzule/) showed that re-ranking so-called "naive" search engines like those that use the BM25 algorithm for retrieval, outperforms moving the data into a vector database for many common NLP tasks such as question answering.

## How does SWIRL Retrieval Augmented Generation (RAG) work?

SWIRL AI Connect also includes state-of-the-art cross-silo [Retrieval Augmented Generation (RAG)](https://en.wikipedia.org/wiki/Retrieval-augmented_generation):

![SWIRL AI Connect Insight Pipeline](images/swirl_rag_pipeline.png)

When a user requests an AI insight, SWIRL:

* Sends the insight out to relevant sources
* Normalizes and unifies the results 
* Re-ranks the united results using non-generative Reader LLM
* Optionally, presents them to the user and allows them to adjust the result set
* Fetches the full-text of the results, in real time
* Identifies the most relevant portions of the documents and binding them to a prompt using real-time vector analysis similar to the re-ranking described above
* Sends the prompt to the approved generative AI for insight generation
* Returns a single set of insights with citations

SWIRL AI Connect includes the Galaxy UI, but includes fully Swagger'd APIs and is easy to integrate with most any front-end or system.

SWIRL AI Connect ENTERPRISE includes flexible, generic OAUTH2 and SSO, with auto-provisioning via OpenID Connect.

## What do SWIRL AI Connect insights look like?

Here is an example:

![SWIRL RAG AI Insight with results](images/swirl_rag_pulmonary_3.png)

TBD
For more information please refer to the [AI Guide](AI-Guide).

## What is SWIRL AI Co-Pilot? 

SWIRL AI Co-Pilot turns any sufficiently capable Generative AI/LLM into an AI assistant that converses with users to determine what they are looking for and where they are most likely to find it. The Co-Pilot can search on the user's behalf and provide in-line RAG results whenever the conversation demands it. 

## How does SWIRL AI Co-Pilot work?

SWIRL AI Co-Pilot educates the designated GAI/LLM about the user and what they have access to via the integration with AI Connect. SWIRL manages the context and history for each chat, initiating RAG through AI Connect as directed by the user and Co-Pilot. The user can only see insight from data they are already authorized to see, and the Co-Pilot is privy only to each user's conversations and history when conversing with them. All access is controlled and provisioned via the existing sign on (SSO) system. 

## What does a conversation with your data via SWIRL AI Co-Pilot look like?

Here is an example:

![Co-Pilot image]()

For more information please refer to the TBD-Guide.

## What is included in SWIRL Enterprise?

SWIRL AI Connect Enterprise includes:

* Configurable support for many enterprise AI providers (e.g. Anthropic and Cohere), including support for multiple GAI/LLMs in different roles - chat, query rewriting, direct answer, RAG and embeddings (for re-ranking/passage detection by the Reader LLM)

* Support for Single Sign On (SSO) with various IDPs (e.g. Ping Federate) and autoprovisioning via OpenID Connect. (The Community version only supports M365.)

* Support for generating AI insights from 1,500 different file formats, including tables and txt in images 

* Authentication support for the PageFetcher

* Configurable prompts, including role, user, group and on-the-fly selection

SWIRL AI Co-Pilot is only available in Enterprise edition, and is not open source. Co-Pilot requires SWIRL AI Connect.

## How much does SWIRL Enterprise cost?

Pricing for SWIRL Enterprise is here: [https://swirlaiconnect.com/pricing](https://swirlaiconnect.com/pricing)

## When should I use SWIRL AI Connect, Community Edition?

Use SWIRL AI Connect, Community Edition, if you have one or more repositories that you want to search and RAG against without authenticating and/or indexing it into yet-another repository and/or writing more code.

You can freely re-distribute SWIRL AI Connect, Community Edition, under the [Apache 2.0 License](https://github.com/swirlai/swirl-search/blob/main/LICENSE).

## When should I use SWIRL AI Connect, Enterprise Edition? 

Use the Enterprise Edition of SWIRL AI Connect when you have:

* Repositories that require Single Sign On (SSO) and/or OAUTH2
* Content that requires text extraction, and/or authenticated page fetching
* The need to RAG from long documents, complex tables, or text from images
* Need to use GAI/LLMs other than OpenAI/Azure OpenAI

## What systems can SWIRL AI Connect integrate with?

The full list is here: [https://swirlaiconnect.com/connectors](https://swirlaiconnect.com/connectors)

## How do I connect SWIRL AI Connect to some new source?

To connect SWIRL with an internal data source, you [create a SearchProvider record](./User-Guide.md#using-searchproviders).

To integrate SWIRL Enterprise with a generative AI, you create an AIProvider record, as described 
[in the Enterprise Guide](./Enterprise-Guide.md#managing-ai-providers).

## Why don't you use GitHub Issues?

We prefer to use [our free Slack channel](https://join.slack.com/t/swirlmetasearch/shared_invite/zt-1qk7q02eo-kpqFAbiZJGOdqgYVvR1sfw) for support.

## What is the SWIRL Architecture & Technology Stack

SWIRL products use the Python/Django/Celery/Redis stack, with PostgreSQL recommended for production deployments.

![SWIRL AI Connect Architecture diagram](images/swirl_arch_diagram.jpg)

## How is SWIRL usually deployed?

SWIRL is usually deployed via Docker. SWIRL Enterprise products are delivered as Kubernetes images. 

## Does SWIRL offer hosting? How can I learn more? 

Please [contact SWIRL](mailto:hello@swirlaiconnect.com) for information about hosted services.

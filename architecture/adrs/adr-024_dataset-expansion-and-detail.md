# ADR 024: Dataset Expansion & Detail

## Context

As we began building our ranking and recommendation agentic workflow, we noticed some limitations with our initial Kaggle-only dataset ([ADR 014](./adr-014_kaggle_dataset_integration.md)). Information on qualitative features (e.g., ambience, dining type, amenities) was limited, making it difficult for context-aware reasoning by an LLM-powered Rank Agent ([ADR-023](./adr-023_basic-rank-agent.md)). To address this, we decided to expand both the depth and breadth of our restaurant metadata.


## Decision

We expanded our restaurant dataset by combining multiple data sources, primarily the Google Places API and Kaggle, to increase both coverage and detail. This integration allowed us to collect new fields such as price level, total reviews, ambience tags, and amenities like “live music” or “outdoor seating.” These additions provide the Rank Agent with more context for generating meaningful recommendations and justifications.

To manage the larger dataset, we standardized the schema in Firestore and implemented data-cleaning scripts to remove duplicates and normalize fields. We also integrated selective caching to avoid redundant API calls, keeping the enrichment process efficient and cost-effective.


## Status

Accepted - 2025-11-12


## Consequences

This expansion should significantly improve the reasoning depth of our Rank Agent, enabling more specific and interpretable recommendations (e.g., “Matches your preference for live-music venues near downtown”). It also helps diversify our dataset, improving the generalizability of test results across cuisine types and locations.

However, the richer dataset will introduce higher storage and maintenance costs, as well as the need for stronger indexing and validation. Moving forward, we plan to build automated data-refresh workflows to maintain consistency. Despite these trade-offs, this change lays a good foundation for scalable, detailed, and explainable recommendations across future releases.

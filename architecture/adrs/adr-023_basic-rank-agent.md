# ADR 023: Basic Rank Agent for Restaurant Recommendations

## Context
As our recommendation system matured beyond static retrieval and keyword search, we needed a mechanism to prioritize and personalize restaurant results. The previous pipeline could retrieve relevant restaurants, but we lacked an interpretive layer to evaluate qualitative restaurant features (e.g., cuisine type, price level, popularity, and ambience tags) against a user’s taste vector profile.

## Decision

Implement a Basic Rank Agent using LangChain to prompt an LLM (e.g., GPT-4-Turbo) with:
- A list of restaurant candidates (retrieved from Firestore or the Places API).
- Structured metadata for each restaurant (name, cuisine, distance, rating, price level, tags, etc.).
- A set of user-specific preference tags (synthetic or derived from onboarding responses).

The agent’s task is to:
- Rank all input restaurants based on alignment with user preferences and overall appeal.
- Return short justifications for the top selections (e.g., “Closer to you and matches your preference for casual Japanese dining”).
- Output a structured JSON list ordered by relevance for the frontend to display in ranked cards.

The LLM prompt design encourages interpretability and lightweight reasoning over raw computation. This design also establishes a foundation for future, more optimized versions of the ranking agent that may assign different types of restaurant features with different weights.

## Status
Accepted — 2025-11-12

## Consequences
- Progress toward CUJs and MVP: This is a significant step toward completing our primary CUJs and a working MVP, as a functioning and reasoning-capable recommendation system ultimately serves as the backbone of our system.
- Interpretability Gains: The system produces human-readable reasoning for each recommendation, facilitating explainable AI behavior and better debugging.
- Future Direction: A planned ADR will document the transition toward a Hybrid Rank Agent, combining LLM interpretability with quantitative user modeling for faster and more scalable ranking.

# ADR 027: User Archetype Profiles & Synthetic Activity Seeds

## Context

Following [ADR 025 (Digital Identity Design)](./adr-025_digital_identity_design.md) and [ADR 026 (Implicit Activity Weighting)](./adr-026_implicit_user_activity_agent_reasoning.md), our recommendation pipeline now integrates both explicit, long-term preference vectors and implicit behavioural signals. However, in order to provide a more structured approach to encoding stable preference patterns, we introduced a system of **six user archetypes** derived from the onboarding questionnaire. These six archetypes include:

- The **Explorer** – seeks novelty, diversity, and less-common cuisines  
- The **Purist** – prefers traditional, authentic, regional-specific cuisine experiences  
- The **Social Curator** – prioritizes ambiance, group suitability, and “shareability”  
- The **Trend Seeker** – enjoys popular, viral, or recently trending restaurants  
- The **Conformist** – prefers safe, widely-liked choices with consistent quality  
- The **Aestheticist** – values plating, interior design, and visual presentation, etc.

We defined these archetypes to capture distinct culinary identities that persist over time. We aim to use these archetypes to complement implicit user activity (likes, saves, dislikes, visits, as mentioned in [ADR 026 (Implicit Activity Weighting)](./adr-026_implicit_user_activity_agent_reasoning.md)) with an explicit, stable representation of an individual's dining personality. Archetypes also introduce opportunities for greater user engagement and interaction by allowing them to talk about their archetypes with others.


## Decision

We incorporated archetype classification as part of the onboarding questionnaire and embedded the archetype label within each user’s digital identity. Thus, the archetype will a) influence the weighting of restaurant metadata (e.g., price, cuisine, popularity, novelty, ambience), and b) serve as a stable modifier in the ranking agent’s reasoning.

Additionally, for development and demonstration purposes, we introduced **synthetic activity seed profiles** that populate demo/test accounts with reproducible implicit behaviour. Each seed is designed to reflect behaviour consistent with an archetype and provide predictable patterns suitable for evaluation, testing, presentations, etc.

Overall, this allows us to evaluate the ranking agent with a fixed, well-defined archetype, a known implicit activity history, and a stable environment for comparing recommendation quality.


## Status

Accepted - 2025-11-18


## Consequences

By integrating archetypes and synthetic activity seeds, we aimed to strengthen both the personalization logic and the reproducibility of our testing pipeline. This decision leads to several consequences downstream:

**Clearer Personalization Layers:** Archetypes now serve as the stable "identity backbone," or overarching "personality" of a user, while implicit activity expresses behavioural shifts that evolve over time. This separation offers a more explainable and transparent logic underlying  our recommendations. 

**Consistent Testing & Demoing:** With synthetic seeds, our demo accounts yield predictable outputs. This allows for more consistent and reliable demonstrations (e.g., two accounts with different archetypes should produce visibly different ranked lists).

**Social Potential:** Users can communicate with others regarding their archetypes, providing a stronger sense of community and engagement within our platform.

**Prompt and Model Adaptations:** The ranking agent must cleanly incorporate archetype traits into its reasoning, which requires adjusted prompt structures and attribute weightings.

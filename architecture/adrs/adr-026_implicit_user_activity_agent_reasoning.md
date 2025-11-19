# ADR 026: Agent Reasoning with Implicit User Activity

## Context

As outlined in [ADR 025](./adr-025_digital_identity_design.md), we decided to have our recommendation platform use two complementary forms of user modelling:
1.	**Explicit reasoning**, based on stable “taste vectors” optionally defined during onboarding  (e.g., cuisine preferences, price sensitivity, dietary needs).
2.	**Implicit reasoning**, derived from behavioural signals accumulated over time (e.g., likes, saves, visits).

The main reasons for this are to reduce the required length of the user onboarding questionnaire, while still having an adaptable, detailed user profile that evolves over time.    

The previous ADR introduced the structure of the digital identity and its metadata fields. This ADR focuses on the implementation of the ranking agent, as well as considerations as to how the agent should “weigh” implicit behavioural data relative to explicit preferences when generating restaurant recommendations.


## Decision

We revised the agent prompt and ranking logic to incorporate a prioritized weighting of implicit user data while maintaining the importance of the user’s stable “taste vector.”


The agent will consider explicit and implicit information in the following order of importance:

1. **Taste Vector (Explicit Preference)** - Represents high-level, relatively stable user traits. This remains the primary anchor for recommendation quality and personalization.

2. **Saved Restaurants** - Indicates strong, deliberate user interest and often signifies a high likelihood of future visitation.

3. **Liked Restaurants** - Signals positive sentiment toward the restaurant’s attributes but with slightly less intent than saved restaurants.

4. **Visited Restaurants** - Reflects exploratory behaviour. It provides useful signals but does not necessarily indicate strong interest or preference alignment.

5. **Disliked Restaurants** - Represents explicit negative sentiment. Restaurants with similar properties should be down-ranked or avoided.

Under this structure, the agent remains aligned with the user’s long-term, overall identity (their taste vector), while still adapting recommendations toward restaurant categories that reflect the user’s interactions with the app (likes, saves, visits, etc.).


## Status

Accepted – 2025-11-18

## Consequences

Overall, this decision strengthens the quality of our personalization pipeline by combining long-term preferences and personality with short-term behavioural signals. However, this required updates to our agent prompts and ranking logic. Key consequences include:

**Improved Personalization:** The agent adapts recommendations based on implicit user behaviour while still making decisions generally based on the user’s explicit, questionnaire-based taste vector.

*Flexibility:** Interactive user actions (e.g., saving, liking, or visiting a restaurant) immediately improve ranking relevance, reducing dependence on our formerly lengthy onboarding flow.

**Greater Explainability:** The explicit hierarchy of information, as presented here in this ADR, provides a transparent rationale for ranking outcomes, which can later support how we justify and explain our recommendations.

**Data Structure Considerations:** User activity metadata must stay consistent across Firestore and ranking computations. This ADR may also inspire future extensions to our recommendation logic (e.g., weighting decay over time, or older user activity being considered less).

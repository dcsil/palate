# ADR 028: Recommendation Output Schema

## Context

With a working basic rank agent ([ADR 023](./adr-023_basic-rank-agent.md)) and more clearly defined agentic reasoning ([ADR 026](./adr-026_implicit_user_activity_agent_reasoning.md) and [ADR 027](./adr-027_user_archetype_profiles.md)), we needed to think about how specifically our agentic reasoning output data should be formatted in order to be usable and interpretable downstream. This is also important in order to maintain consistent communication between the frontend andbackend.


## Decision

We defined a standard JSON schema for our ranking agent outputs. All recommendation endpoints that use the ranking agent must return a payload of the following shape:
```
{
    "ranked_restaurants": [
        {
            "restaurant": {
                “name”: …
                “rating”: …
                [other optional metadata]		
            },
            "justification": "This restaurant is a great fit for you because..."
        },
        ..
    ],
    "total_restaurants": int
}
```
Therefore, each output from the ranking agent contains a ranked list of restaurants, each populated with metadata that canbe used by our frontend. Justifications are also included and offered from a second-person perspective (i.e., as if talking directly to the user instead of saying something like "This restaurant is a great fit for the user because...") such that it can be used immediately by our user interface.

## Status

Accepted - 2025-11-18

## Consequences

Overall, standardizing the recommendation output schema strengthens the reliability and clarity of backend–frontend communication andmarks a major step in a full end-to-end recommendation workflow. Key consequences include:

**Consistent Integration Across the Stack:** The frontend can now has a well-defined contract for rendering restaurant cards, justifications, and list ordering.

**Support for Future Explainability Features:** The inclusion of a `justification` field enables transparent recommendation reasoning. This can later support features such as “Why this restaurant?”, archetype-based explanations, or social-comparison components.

**Backwards Compatibility and Future Extensions:** Optional metadata fields allow us to cleanly add new attributes (e.g., cuisine tags, dietary filters) as long as required fields remain consistent.

**Prompt Adjustments Required:** The prompt passed on to the ranking agent must be modified to ensure that the returned structured JSON that conforms to this schema. Also, post-processing logic must be implemented (e.g., with Pydantic) in order to validate output before returning it via our API.

Overall, defining a standard schema significantly improves the stability, interpretability, and extensibility of our recommendation pipeline, and provides a strong foundation for our app's end-to-end processes.

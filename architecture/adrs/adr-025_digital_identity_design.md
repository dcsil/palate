# ADR 025: Digital Identity ("Palate") Formation Strategy

## Context

- Our original digital identity model relied on a long onboarding questionnaire that assigned users into six archetypes:
  - Explorer
  - Purist
  - Social Curator
  - Trend Seeker
  - Conformist
  - Aestheticist
- Recommendations were largely based on this static archetype classification.
- Early testing revealed several issues:
  - High drop-off rates during onboarding
  - Low conversion from sign-up to active usage
  - Archetypes felt rigid and did not adapt as user preferences changed
  - Long forms created friction before users experienced any product value
- To improve activation and retention, we revisited how a user’s “palate” should be constructed with a focus on:
  - Shortening onboarding
  - Allowing preferences to evolve dynamically
  - Leveraging implicit behavioral signals instead of relying solely on survey responses

## Decision

- Transition from a survey-heavy onboarding flow to a hybrid implicit-first digital identity system.
- Core components of the new approach:
  - The system now uses implicit behavioral signals as the primary driver of preference inference:
    - Likes, saves, and bookmarks
    - Scroll and swipe interactions
    - Search behavior
    - Restaurant views and engagement patterns
  - These signals continuously update the user's palate over time.
- A questionnaire still exists but:
  - Is optional
  - Contains only a small number of high-impact questions (e.g., dietary restrictions, strong dislikes)
  - No longer blocks the user from entering the app immediately
- Archetypes now function as soft preference dimensions rather than rigid user categories.
- The digital identity becomes adaptive, growing based on real user behavior rather than static upfront inputs.

## Status

Accepted — 2025-11-12

## Consequences

- Expected benefits:
  - Lower friction during onboarding and higher completion rates
  - Recommendation quality improves as behavioral signals accumulate
  - More accurate and adaptive user profiles that reflect changing preferences
  - Supports long-term personalization across different contexts and group settings
- Trade-offs:
  - Increased engineering complexity in event instrumentation and preference modeling
  - Cold-start problem is reduced but not eliminated
  - Requires clearer communication around data usage and privacy
- Overall, this hybrid identity model provides a scalable foundation for dynamic, behavior-driven personalization across future releases.

# ADR 025: Digital Identity ("Palate") Formation Strategy

## Context

Our original digital identity model relied on a long onboarding questionnaire that assigned users into six archetypes. The "Explorer," the "Purist," the "Social Curator," the "Trend Seeker," the "Conformist," and the "Aestheticist."   

Initially, we planned to offer recommendations based on this static archetype classification. However, user research with two classmates revealed several issues. Specifically, long questionnaires had the potential to increase cognitive load and reduce interest in completing onboarding. Therefore, we risk:
- Drop-off rates during onboarding
- Low conversion from sign-up to active usage
Furthermore, assigning all users to only six categories felt rigid and would mean that the app could not adapt even as user preferences changed
Therefore, to improve activation and retention, we revisited how a user’s “palate” should be constructed with a focus on:
- Shortening onboarding
- Allowing preferences to evolve dynamically
- Leveraging implicit behavioral signals instead of relying solely on survey responses

## Decision

To maintain user interest and attention spans during onboarding, we decided to transition from a survey-heavy onboarding flow to a hybrid, implicit and explicit digital identity system. Core components of the new approach include:
- The use of implicit behavioral signals as a main driver of preference inference; for example:
  - Likes, saves, and bookmarks
  - Scroll and swipe interactions
  - Search behavior
  - Restaurant views and engagement patterns

These signals continuously update the user's palate over time.
- An onboarding questionnaire still exists, but:
  - This is now optional
  - Contains only a small number of high-impact questions (e.g., dietary restrictions, strong dislikes)
  - No longer blocks the user from entering the app immediately
- Archetypes now function as soft preference dimensions rather than rigid user categories.

Therefore,  digital identity becomes adaptive, growing based on real user behavior rather than static upfront inputs.

## Status

Accepted — 2025-11-12

## Consequences
Expected benefits to this digital identity formation strategy include:
- Lower friction during onboarding and higher completion rates
- Recommendation quality improves as behavioral signals accumulate
- More accurate and adaptive user profiles that reflect changing preferences
- Supports long-term personalization across different contexts and group settings

However, some trade-offs include:
- Increased engineering complexity in event instrumentation and preference modeling
- Cold-start problem is reduced but not eliminated
- Requires clearer communication around data usage and privacy

Nonetheless, this hybrid identity model provides a scalable foundation for dynamic, behavior-driven personalization across future releases.

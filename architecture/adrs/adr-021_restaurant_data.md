# ADR-021: Restaurant Owner Verification and Data Ownership

**Date:** 2025-11-08  
**Status:** Accepted  
**Deciders:** Core Engineering Team (Product, Backend)  
**Context:** Palate App (Restaurant Discovery Platform)

---

## 1. Context

Currently, all restaurant data (metadata, menus, images, reviews, tags, etc.) in Palate is sourced from public APIs (Google Places) and internal enrichment pipelines. However, this approach limits data accuracy, freshness, and authenticity—especially for fast-changing attributes such as menus, promotions, and ambience tags.

To enhance data reliability and strengthen the platform’s credibility, we propose allowing **restaurant owners to claim ownership of their business profiles**. Once verified, the **restaurant owner becomes the primary data steward** of that listing, with the ability to update and manage their information directly through an authenticated portal.

---

## 2. Decision

We will introduce a **Restaurant Owner Verification & Data Control System**, enabling verified owners to manage their listings independently.

### Key Components

1. **Claim Ownership Flow**
   - Owners search for their restaurant on Palate.
   - Verification via business email domain (e.g., `@restaurantname.com`), phone number, or manual document submission (business license).
   - Admin approval process for edge cases.

2. **Ownership Model in Database**
   - New Firestore collection or subcollection: `/restaurants/{restaurantId}/ownership`
   - Fields: `owner_uid`, `verified_status`, `claimed_date`, `verification_method`, `last_verified_at`
   - Once verified, a boolean flag `isOwnerManaged = true` is set in the main restaurant document.

3. **Data Control Logic**
   - When `isOwnerManaged = true`, updates to that restaurant’s data come **only from the owner’s portal**.
   - System and crowd-sourced updates (e.g., via AI enrichment or user reports) will enter a moderation queue for the owner’s approval.

4. **Owner Portal**
   - A web dashboard (integrated or separate) allowing restaurant owners to:
     - Edit restaurant information (menu, images, opening hours, tags).
     - View analytics on user visits, saves, and interactions.
     - Respond to user feedback or suggestions.

---

## 3. Alternatives Considered

| Option | Description | Pros | Cons |
|--------|--------------|------|------|
| **Crowdsourced edits only** | Continue allowing user-reported edits validated by admins | Low implementation cost | Poor data accuracy, prone to spam |
| **Third-party data sync (Google/Yelp)** | Rely on synced updates from partners | Consistent baseline | No brand control, limited real-time updates |
| **Owner verification (chosen)** | Allow verified owners to self-manage data | High trust, authentic, scalable | Requires moderation, identity verification overhead |

---

## 4. Consequences

### Pros
- Increases **data authenticity and freshness**  
- Establishes **trust and accountability** between restaurants and users  
- Opens up **B2B monetization opportunities** (e.g., premium analytics, ads)  
- Reduces dependency on third-party APIs for dynamic content  

### Cons / Risks
- Requires a **robust verification process** to prevent fraudulent claims  
- Increases **backend and operational complexity** (moderation queue, permissions)  
- Possible **inconsistency** if owners abandon claimed listings without maintenance  
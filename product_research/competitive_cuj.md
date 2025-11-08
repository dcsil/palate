# A7 CUJ Runthrough + Demo of Google Maps & Reviews
In this document, we discuss our step-by-step experience using Google Maps & Reviews. We include recommendations for improvement, discussions regarding the most difficult steps, as well as areas of improvement.

### Submission Date: 11/06/2025

## Team Information
### Team Name – Palate   
Franco Miguel Valencia – 1009486771   
Jisung Shin – 1004192170

## TL;DR
Google Maps and Google Reviews are accessible and intuitive tools for restaurant discovery, offering extensive information like reviews, photos, and business details. However, they **lack personalization** and thus require **frequent switching** between social apps and websites to compare options and share information. This fragmentation matters because it increases decision fatigue. Our product should centralize discovery and decision-making to reduce context switching and improve group coordination.
<br>

## Our User Goal
***“As a university student who loves exploring new spots with friends, I want to find restaurants that match our group’s vibe, so that I can spend less time deciding and more time enjoying the moment.”***

## Summary of Findings

### User Persona
The **Social Explorer** represents Gen-Z adults (18–24) in urban areas who eat out frequently, often 2-3+ times per week. For them, dining is not just about food; it is about the vibe, ambiance, and matching the energy of the group.

They are digitally fluent users of TikTok, Instagram, and Google Maps. They are familiar with tools like Yelp, OpenTable, and Google Reviews, but experience low satisfaction because discovery requires stitching together multiple platforms; for example, Google for logistics, TikTok/Instagram for visuals, and WhatsApp for group decision-making. They are not loyal to any one product and want personalized recommendations that “get” their preferences — not just what is popular.


### Tools Used
- Group Chat (WhatsApp) – for coordinating with friends and sharing links.
- Google Maps & Google Reviews – for nearby restaurant locations, reviews, and hours.
- TikTok and Instagram – for discovering trending restaurants and visuals.
- Google Search – gateway to Google Maps and Places results.


### Highlights and Lowlights

| **Category** | **Tasks** | **Description** | **Severity / Difficulty** |
|--------------|------------|----------------------------------|----------------------------|
| **Group Coordination & Planning** | Steps 1–3 | Group chat coordination worked well for starting plans, but consensus-building was messy. Messages got buried quickly and comparing multiple links across chats was inefficient. | **Moderate** |
| **Discovery & Inspiration** | Steps 4–6 | TikTok/Instagram provided inspiration, while Google Maps made it easy to search logistics. However, platform switches were *very frequent* and some information (e.g., crowd level, parking) was inconsistent. | **Severe** |
| **Information Validation** | Steps 7–8 | Menus and dietary options were difficult to confirm. Links often led to outdated PDFs or incomplete data, and external websites had to be visited in order to find this information. Keyword searches for “vegan” or “halal” in reviews returned unreliable results. | **Severe** |
| **Decision-Making** | Steps 9 | The group used emoji votes in WhatsApp to finalize choices. While simple, this method was prone to bias (e.g., duplicates) and missing input from late voters. | **Moderate** |
| **Booking & Confirmation** | Steps 10-11 | Reservation redirections to third-party apps added friction, and final details got lost in chat noise. Reconfirmations were common because key details were lost in group chat noise. | **Severe** |


### For Google Maps & Reviews (Product Improvements):
- Introduce contextual filtering options such as mood or ambiance (“quiet,” “outdoor-friendly”...).
  
***Why?*** During our CUJ, we observed that users had to leave Google Maps and open TikTok or Instagram to assess the *vibe* of a place. Current Google Reviews filters prioritize logistics (e.g., price, opening hours) but neglects information related to the experience.

- Enhance the review surfacing system to prioritize descriptive, high-quality reviews with sentiment scoring.

***Why?*** We had to scan multiple long reviews to infer ambiance and menu quality. Many reviews were noisy and only a few conveyed vibe. Thus, applying sentiment scoring to highlight "key words" would improve consistency and reduce context switches.

- Allow group collaboration features, such as shared shortlists or in-app polls, to streamline collective decision-making.

***Why?*** Google maps forces users into WhatsApp or another app to compare options and vote. Most of our 29 context switches were due to group coordination.

### For Future Users (Behavioral Recommendations):
- Combine Google Reviews with social platforms (TikTok or Instagram) for better visual context.

***Why?*** Photos on Google Reviews are often out of date or poorly taken.

- Bookmark or create custom lists on Maps to track favorite places.

***Why?*** Instead of re-discovering the same restaurants every time, users can build a recurring shortlist. This reduces total time spent discovering new restaurants.

- When coordinating in groups, use a shared Google Map list rather than long chat threads to save time.

***Why?*** Sending individual links in WhatsApp led to buried messages and repeated scanning. Shared lists consolidate options and reduce friction.


## Competitor Product Analysis

Google Maps & Google Reviews are strong, widely-used tools for restaurant discovery, and our CUJ revealed clear strengths. Their biggest advantage is data completeness: **nearly every restaurant** has photos, reviews, business hours, and real-time closure updates (e.g., “closed now”). The interface is familiar and intuitive, making early-stage discovery smooth. Search is fast, the visual map metaphor helps with spatial planning, and features like Street View and navigation are delightful because they reduce uncertainty before leaving. In short, Google excels at logistics.

However, the CUJ exposed critical weaknesses for our persona (the Social Explorer). Once a user moves beyond logistics into decision-making - “Which place matches our group’s vibe?” - Google Reviews becomes much less effective. It lacks contextual filtering (e.g., “cozy,” “good for groups,” etc.), **forcing users into TikTok and Instagram** to assess ambiance. Furthermore, reviews are unstructured, menu links may lead to outdated PDFs, and voting occurs in WhatsApp. During our CUJ, this caused 29 context switches across 4 apps and third-party restaurant websites to verify and share information. Ultimately, settling upon a decision was frustrating, slow, and mentally taxing, resulting in decision fatigue.

Hence, Palate will not compete on breadth of data or navigation - Google already dominates that problem space. Instead, Palate differentiates on depth of personalization and group decision-making. Palate will provide vibe-based filtering that describe **atmosphere** and **energy**, not just menu quality. Furthermore, in addition to group-wide recommendations, this CUJ inspired us to consider implementing **interactive social dashboards** to reduce context switches with Google Maps and WhatsApp.

Overall, Palate intentionally avoids replicating Google’s mapping features. Our value lies in reducing cognitive load by **centralizing** discovery and decision-making, so users no longer need Google Maps for logistics, TikTok for vibe, and WhatsApp for consensus. Palate becomes the place where decisions actually get made.

### CUJ Overview Table
| **Phase**                  | **Steps** | **Estimated Time to Complete** | **Context Switches** |
| -------------------------- | --------- | ------------------------------ | -------------------- |
| **Group Coordination**     | 1–3       | ~15–20 min                     | 6                    |
| **Discovery & Research**   | 4–6       | ~25–30 min                     | 12                   | 
| **Information Validation** | 7–8       | ~20 min                        | 10                   | 
| **Decision-Making**        | 9         | ~10–15 min                     | 1                    |
| **Booking & Confirmation** | 10-11     | ~15–20 min                     | 4                    |

**Total Time**: ~85–105 minutes (1.5 hours)   
**Total Context Switches**: ~29   
**Overall Experience**: A smooth start with group coordination. Google Reviews and Maps were intuitive to use, and every restaurant we examined was searchable on these platforms. However, there was high friction during restaurant discovery, information validation, and booking due to fragmented information, limited recommendation personalization, and group chat noise burying key details. A lot of context switching led to frustration and wasted time.


### End-to-End User Journey Documentation

| **Step** | **Notes** | **Screenshot** |
|-----------|------------|----------------|
| **1. Reach out to the group** | Created a WhatsApp group thread and polled for availability among friends. | ![screenshot1](./comp_cuj_assets/Picture1.jpg) |
| **2. Determine the occasion & vibe** | Agreed on “casual & cozy" as the mood for the outing. | ![screenshot2](./comp_cuj_assets/Picture2.jpg) |
| **3. Initial idea dump (share first options)** | Friends pasted Google Maps links and TikTok/Instagram posts into the chat. | ![screenshot3](./comp_cuj_assets/Picture3.jpg) |
| **4. Scan trending options and send to group chat** | Browsed TikTok and Instagram for “Pho places near UofT" and saved 3 reels as references, switching to the group chat to send links along with a short description of each. | ![screenshot4](./comp_cuj_assets/Picture4.jpg) |
| **5. Check real details (hours, busy times)** | Based on the links sent in the group chat, clicked through Google Search results to Maps listings for reviews and hours. | ![screenshot5](./comp_cuj_assets/Picture5.jpg) |
| **6. Confirm location convenience** | Reviewed each restaurant's distance from campus and checked transit/parking availability on Google Maps. | ![screenshot6](./comp_cuj_assets/Picture6.jpg) |
| **7. Menu and price sanity check** | Checked menus through Google Maps and restaurant websites; noticed menu info from a year ago that could potentially be outdated. Had to visit an external restaurant website in order to validate this information. | ![screenshot7](./comp_cuj_assets/Picture7.jpg) |
| **8. Dietary constraints pass** | Used Google Search and Maps to verify gluten free options; relied on keywords in reviews. | ![screenshot8](./comp_cuj_assets/Picture8.jpg) |
| **9. Quick confirmation (vote)** | Used emoji reactions in WhatsApp to vote and finalize the restaurant. | ![screenshot10](./comp_cuj_assets/Picture9.jpg) |
| **10. Reservation check** | Looked for the “Reserve” button in Google Maps, but this button was not found. Instead, used "Phone." Calling the restaurant revealed that the restaurant does not take reservations. | ![screenshot12](./comp_cuj_assets/Picture10.jpg) |
| **11. Final confirmation** | Pinned the chosen restaurant’s address and meeting time in the WhatsApp chat. | ![screenshot14](./comp_cuj_assets/Picture11.jpg) |

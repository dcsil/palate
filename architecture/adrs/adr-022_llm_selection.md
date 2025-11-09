# ADR-022: Migration from OpenAI API to Gemini 2.5 Flash

**Date:** 2025-11-08  
**Status:** Proposed  
**Deciders:** Core Engineering Team (Product, Backend)  
**Context:** Palate App (AI Recommendation and Analysis System)

---

## 1. Context

The current AI capabilities of Palate such as user preference analysis, restaurant ranking, and conversational recommendations—are powered by OpenAI’s GPT models. While these models provide strong performance and natural language understanding, the cost and latency have become increasingly significant.

Additionally, Palate’s backend and infrastructure already operate within the **Google Cloud ecosystem** (Firestore, Cloud Run, Pub/Sub, Vertex AI), creating a fragmented architecture by relying on an external LLM provider.

To improve cost efficiency, latency, and ecosystem integration, we propose transitioning from **OpenAI API** to **Gemini**, especially Gemini 2.5 flash, Google’s latest multimodal foundation model.

---

## 2. Decision

We will **migrate LLM-powered features** from OpenAI GPT models to **Gemini 2.5 Flash**, hosted within our existing Google Cloud project.

The migration will include:
- **Text-based reasoning** tasks (e.g., generating restaurant summaries, classification, and re-ranking)
- **Conversational recommendations** within the user chat experience
- **AI enrichment pipelines** that augment restaurant metadata and ambience vectors

### Rationale
1. **Speed:** Gemini 2.5 Flash is optimized for ultra-low latency and streaming outputs.  
2. **Performance:** Provides competitive reasoning and text generation quality comparable to GPT-4o-mini, GPT-4.1-mini, or GPT-5-mini models.  
3. **Cost Efficiency:** We can leverage **free Google Cloud credits** and integrated billing through our startup program.  
4. **Ecosystem Integration:** Seamless connection with Vertex AI, Cloud Functions, Cloud Run, and service accounts—reducing authentication complexity.  

---

## 3. Alternatives Considered

| Option | Description | Pros | Cons |
|--------|--------------|------|------|
| **Continue using OpenAI** | Maintain current GPT-4-turbo integration | Familiar, stable API | High cost, external dependency |
| **Migrate fully to Gemini (chosen)** | Replace all LLM calls with Gemini 2.5 Flash | Unified ecosystem, lower latency, cost savings | Requires prompt re-tuning and testing |

---

## 4. Consequences

### Pros
- Reduced **latency** and faster response times for user interactions  
- **Lower costs** due to use of Google Cloud startup credits  
- Simplified **authentication and deployment** under existing IAM structure  
- Easier **scaling and monitoring** using Google Cloud’s integrated tools  
- **Future-proof** as Gemini continues to improve multimodal capabilities (images, audio, video)

### Cons / Risks
- Requires **prompt re-tuning** and validation of outputs due to model differences  
- Slight **feature gap** in fine-tuned reasoning vs GPT-4o-mini for niche tasks  

---

## 5. Implementation Notes

### Integration Plan
1. **Model API**
   - Use langchain's built-in LLM wrapper.
2. **Environment**
   - No new API keys required — uses **service account credentials**.
   - Deploy alongside Cloud Run and Firestore using the same GCP project.

3. **Prompt Migration**
   - Re-tune system prompts and temperature parameters for Gemini’s output style.
   - Validate output consistency for each feature: classification, summarization, and chat.
---

## 6. Decision Outcome

**Status:** Pending

We will begin testing Gemini 2.5 Flash on internal staging for the **AI restaurant recommender** module and **user-agent chat**.  
If results meet or exceed OpenAI’s benchmarks in latency, coherence, and quality, Gemini will become the **primary production LLM** for Palate.

---

## 7. Future Considerations

- Explore **Gemini 2.5 Pro** for high-complexity tasks requiring deeper reasoning.  
- Evaluate **Gemini multimodal input (image/text)** capabilities for menu and ambience analysis.

---

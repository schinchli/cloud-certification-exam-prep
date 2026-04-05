# Google Cloud Generative AI Leader Certification

This folder contains comprehensive study materials for the Google Cloud Generative AI Leader certification exam.

## Contents

- `Google-Cloud-Generative-AI-Leader-Complete-Study-Guide.md` - Complete study guide covering all exam domains

## Exam Overview

The Google Cloud Generative AI Leader certification validates expertise in generative AI concepts, Google Cloud's AI offerings, and business strategies for implementing AI solutions.

### Domain Breakdown

| Domain | Weight | Topics |
|--------|--------|--------|
| **1. Fundamentals of Generative AI** | ~25% | Data types, ML approaches, AI landscape, model characteristics |
| **2. Google Cloud's Gen AI Offerings** | ~30% | Gemini, Vertex AI, AI APIs, infrastructure |
| **3. Techniques to Improve Model Output** | ~25% | Prompting, RAG, fine-tuning, grounding |
| **4. Business Strategies** | ~20% | Responsible AI, data quality, implementation |

### Key Concepts to Master

#### Foundation Models
| Model | Type | Use Case |
|-------|------|----------|
| **Gemini** | Multimodal | Text, code, images, video - most capable |
| **Imagen** | Text-to-Image | High-quality image generation |
| **Veo** | Text-to-Video | Video content creation |
| **Gemma** | Open LLM | Lightweight, developer-friendly |

#### Vertex AI Platform
| Service | Purpose | Key Feature |
|---------|---------|-------------|
| **Model Garden** | Model hub | Discover and deploy models |
| **AutoML** | Automated training | Build custom models without ML expertise |
| **Vertex AI Search** | Enterprise search | RAG-enabled search and recommendations |
| **Agent Builder** | AI agents | Build conversational agents |
| **AI Studio** | Production dev | Enterprise-grade deployment |

#### Output Improvement Techniques
| Technique | When to Use | Key Benefit |
|-----------|-------------|-------------|
| **Prompt Engineering** | Always first | No training needed |
| **Few-Shot Prompting** | Need format/style | Shows examples in prompt |
| **Chain-of-Thought** | Complex reasoning | Step-by-step thinking |
| **RAG** | Need current info | No model retraining |
| **Fine-Tuning** | Domain-specific | Embeds knowledge in model |
| **Grounding** | Reduce hallucinations | Verifiable sources |

### Exam Details

| Attribute | Value |
|-----------|-------|
| **Duration** | 90 minutes |
| **Questions** | ~50 multiple choice |
| **Passing Score** | ~70% |
| **Cost** | $99 USD |
| **Validity** | 3 years |
| **Prerequisites** | None |

## Study Approach

### Phase 1: AI Fundamentals (Week 1)
- Data types (labeled/unlabeled, structured/unstructured)
- ML approaches (supervised, unsupervised, reinforcement)
- ML lifecycle stages
- Gen AI landscape layers

### Phase 2: Google Cloud AI (Week 2)
- Foundation models (Gemini, Imagen, Veo, Gemma)
- Vertex AI platform components
- AI APIs and specialized services
- Google AI Studio vs Vertex AI Studio

### Phase 3: Techniques (Week 3)
- Prompt engineering strategies
- Temperature and sampling parameters
- RAG vs fine-tuning decisions
- Grounding and HITL

### Phase 4: Business & Practice (Week 4)
- Responsible AI principles
- Data quality dimensions
- Success metrics
- Practice questions

## Critical Exam Topics

### Key Differentiators

**Google AI Studio vs Vertex AI Studio:**
- AI Studio: Quick prototyping, free, web-based
- Vertex AI Studio: Production, enterprise-grade, scalable

**RAG vs Fine-Tuning:**
- RAG: External knowledge retrieval, no training, updatable
- Fine-tuning: Embeds knowledge in model, requires training

**Labeled vs Unlabeled Data:**
- Labeled: Has tags/categories → Supervised learning
- Unlabeled: No tags → Unsupervised learning

**Temperature Settings:**
- Low (0.0-0.3): Factual, deterministic, legal/technical content
- High (0.7-1.0): Creative, diverse, brainstorming

### Data Type Quick Reference

| Characteristic | Data Type |
|----------------|-----------|
| Has labels/tags | Labeled Data |
| No labels | Unlabeled Data |
| Tables/databases | Structured Data |
| Text/images/audio | Unstructured Data |

### ML Approach Selection

| Goal | Approach |
|------|----------|
| Classify with labels | Supervised Learning |
| Find patterns, no labels | Unsupervised Learning |
| Learn from rewards | Reinforcement Learning |
| Complex patterns | Deep Learning |

### Common Question Patterns

1. **Data Type Identification**
   - Look for: labels, structure, format
   - Keywords: "manually assigned," "free-form," "tables"

2. **Service Selection**
   - Match requirements to capabilities
   - Consider: ease of use, customization, scale

3. **Technique Application**
   - Prompting first, then RAG, then fine-tuning
   - HITL for high-stakes decisions

4. **Responsible AI**
   - Fairness, explainability, accountability
   - High-stakes needs HITL and explainability

5. **Performance Issues**
   - Degrading → Check for drift
   - Outdated info → Knowledge cutoff or RAG
   - Inaccurate → Grounding or fine-tuning

## Success Tips

1. **Understand Layers**: Know the AI landscape (infrastructure → models → platforms → applications)
2. **Compare Services**: Know when to use AutoML vs custom training vs pre-trained APIs
3. **Prompting First**: Always try prompt engineering before more complex techniques
4. **Responsible AI**: Understand fairness, accountability, transparency principles
5. **Business Focus**: This is a leader cert - think business outcomes, not just technical details

## Recommended Resources

### Google Materials
- [Google Cloud Generative AI Learning Path](https://cloud.google.com/learn/certification)
- [Vertex AI Documentation](https://cloud.google.com/vertex-ai/docs)
- [Google Cloud Skills Boost](https://www.cloudskillsboost.google/)

### Hands-On
- Google AI Studio for prototyping
- Vertex AI for production workflows
- Colab notebooks for experimentation

Good luck with your certification!

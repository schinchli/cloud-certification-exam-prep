# AWS Certified AI Practitioner Study Guide

## Table of Contents
1. [Core AWS AI/ML Services](#core-aws-aiml-services)
2. [Amazon Bedrock & Foundation Models](#amazon-bedrock--foundation-models)
3. [Amazon SageMaker Ecosystem](#amazon-sagemaker-ecosystem)
4. [Generative AI Concepts](#generative-ai-concepts)
5. [Model Training & Evaluation](#model-training--evaluation)
6. [Security & Governance](#security--governance)
7. [Amazon Nova Models](#amazon-nova-models)

---

## Core AWS AI/ML Services

### Amazon SageMaker
**Fully managed service for ML lifecycle** - prepare, build, train, and deploy ML models

### Amazon Bedrock
**Fully managed foundation model service**
- Access to FMs from Amazon and leading AI companies via API
- Built-in security, privacy, and responsible AI capabilities
- Private customization with your own data
- **Knowledge Base** = Bedrock's RAG implementation

### Amazon Rekognition
**Image and video analysis service**
- Content moderation for inappropriate content
- Custom object detection (logos, brands) with AutoML
- Works with drawings, paintings, animations

### Amazon Comprehend
**Natural Language Processing service**
- Entity recognition, key phrase extraction
- Language detection, sentiment analysis
- PII detection and redaction
- Custom and built-in models

### Amazon Textract
**Document analysis service**
- Extract text, handwriting, layout elements
- Works with any document format

### Amazon Transcribe
**Speech-to-text service**
- Automatic language detection
- Multi-speaker identification
- Audio to script conversion

### Amazon Translate
**Language translation service**
- Supports 75+ languages

### Amazon Polly
**Text-to-speech service**
- High-quality, natural-sounding speech
- Multiple languages supported
- Least operational overhead for TTS

### Amazon Lex
**Conversational AI service**
- Voice and text chatbots
- Natural language understanding
- Conversational interfaces

### Amazon Kendra
**Intelligent document search**
- Semantic and contextual understanding
- Provides specific answers to questions

### Amazon Forecast
**Time series forecasting**
- Predicts future data points

### Amazon Personalize
**Recommendation engine**
- Low-code ML service
- Custom recommendations via API

---

## Amazon Bedrock & Foundation Models

### Guardrails for Amazon Bedrock
**Additional safety layer for FMs**
- Evaluates user inputs and FM responses
- Blocks undesirable content
- Prevents hallucinations
- Redacts sensitive/PII information

### Amazon Bedrock Knowledge Bases
**RAG implementation for Bedrock**
- Provides contextual information from private data
- Delivers more relevant, accurate responses
- Integrates company data with FMs

### Amazon Q Business
**Generative AI virtual assistant**
- Answer questions, summarize content
- Generate content and complete tasks
- Based on provided data
- **Note**: Does NOT provide direct access to FMs

### Amazon Q Developer
**AI-powered code assistant**
- Generative AI for software development

---

## Amazon SageMaker Ecosystem

### SageMaker Data Wrangler
**Data preparation and feature engineering**
- Data selection, cleaning, exploration, visualization
- SQL support for data queries
- Data Quality tool for analysis
- **Balancing operators**: Random undersampling, oversampling, SMOTE

### SageMaker Canvas
**No-code ML model building**
- Build ML models without coding
- **Limitation**: No content moderation for creative content

### SageMaker Ground Truth
**Data labeling service**
- Human workforce for accurate labels
- Integration with Amazon Mechanical Turk
- **Note**: Does NOT store model training/performance info

### SageMaker Model Monitor
**Model performance monitoring**
- Automated alerts for quality variations
- Data drift and anomaly detection
- Ensures stable model performance over time

### SageMaker Studio
**Integrated development environment**
- JupyterLab, RStudio, Visual Studio Code support

### SageMaker Model Cards
**Model documentation and governance**
- Record ML model information
- Training details, risk ratings, evaluation metrics
- Part of SageMaker Model Registry

### SageMaker Clarify
**Bias detection and explainability**
- Identify potential bias in models/datasets
- Uses SHAP, Partial Dependency Plots
- Feature attribution based on Shapley values

### SageMaker JumpStart
**ML model hub**
- Open-source and proprietary foundation models

### SageMaker HyperPod
**Distributed training optimization**
- Reduce training time by up to 40%
- Scale across 1000+ AI accelerators

### SageMaker Model Registry
**Model catalog management**
- Version control, metadata association
- Model approval status management

### SageMaker Model Dashboard
**Centralized model portal**
- View, search, explore all account models

### SageMaker Debugger
**Training optimization**
- Debug and optimize ML models
- Real-time monitoring and profiling

### SageMaker Autopilot
**Automated ML (AutoML)**
- Simplifies model building for application owners

### SageMaker Feature Store
**Feature management repository**
- Store, share, manage ML features
- Features used in training and inference

### SageMaker Inference Options
- **Real-time**: Fully managed, autoscaling endpoints
- **Serverless**: Deploy without managing infrastructure
- **Asynchronous**: Queue large requests (<1GB)
- **Batch Transform**: Offline/batch inference

---

## Generative AI Concepts

### Retrieval Augmented Generation (RAG)
**Enhance LLM outputs with external knowledge**
- References authoritative knowledge base
- Outside of training data sources
- Improves accuracy and relevance

### Fine-Tuning Types

#### Fine-Tuning (General)
- Further training on specific tasks/domains
- Requires labeled dataset
- **Benefits**: Increased specificity, improved accuracy, reduced bias, boosted efficiency

#### Continued Pre-Training
- Uses unlabeled, domain-specific data
- Costly and requires expertise

#### Instruction-Based Fine-Tuning
- Uses labeled prompt-response pairs
- Formatted as instructions
- Improves domain-specific performance

#### Domain Adaptation Fine-Tuning
- Improves performance in specific domains
- Uses labeled domain data

#### Transfer Learning
- Reuse model from one task for another
- Take FM and create custom model via fine-tuning

### Prompt Engineering

#### Chain of Thought
- Breaks complex questions into smaller parts
- Recommended for arithmetic and logical reasoning

#### Negative Prompting
- Guide model to avoid certain outputs/behaviors

#### Prompt Templates
- Predefined formats for standardized inputs/outputs

#### Stop Sequences
- Tokens/phrases that instruct model to cease generation

### Model Parameters

#### Temperature
- Controls randomness/diversity of outputs
- **Higher**: More diverse, unpredictable responses
- **Lower**: More deterministic, repetitive responses

#### Top K
- Limits selection to K most probable tokens
- Controls balance between diversity and predictability

#### Top P (0-1 scale)
- Controls diversity by limiting word selection
- **Low (0.25)**: Top 25% probability - focused, coherent
- **High (0.99)**: Top 99% probability - diverse, creative

---

## Model Training & Evaluation

### Learning Types

#### Supervised Learning
- Trained on labeled datasets
- Input paired with correct output
- Goal: Learn input-output mapping

#### Unsupervised Learning
- Trained on unlabeled data
- Discover hidden patterns/structures
- Used for clustering, dimensionality reduction

#### Semi-Supervised Learning
- Combines labeled and unlabeled data
- Small labeled + large unlabeled datasets

### Training Concepts

#### Epoch
- Single complete pass through entire training dataset

#### Learning Rate
- Controls parameter update step size
- Determines training speed

#### Overfitting
- Performs well on training, fails on new data
- **Characteristics**: Low bias, high variance

#### Underfitting
- Too simple to capture underlying patterns
- **Characteristics**: High bias, low variance

#### Ideal Model
- **Low bias, low variance**
- Prevents both overfitting and underfitting

### Feature Engineering

#### Feature Extraction
- Create new features by transforming/combining original features

#### Feature Selection
- Choose subset of most relevant features
- Reduces dimensionality

### Evaluation Metrics

#### Classification Metrics
- **Accuracy**: Correct predictions / All predictions
- **Precision**: True positives / (True positives + False positives)
- **F1 Score**: Balances precision and recall (2 * P * R / P + R)

#### Regression Metrics
- **MSE**: Mean Squared Error - average squared differences
- **MAE**: Mean Absolute Error - average absolute differences
- **RMSE**: Root Mean Squared Error - standard deviation of errors
- **MAPE**: Mean Absolute Percentage Error
- **R²**: Proportion of variance explained by model (0-1)

#### Text Generation Metrics
- **ROUGE**: Quality of summaries/translations vs reference
- **BLEU**: Similarity between generated and reference translations
- **BERT**: Evaluates semantic similarity and meaning

### Model Architectures

#### Transformers
- Neural network architecture for sequence transformation
- Learns context and relationships between components

#### GAN (Generative Adversarial Network)
- Two competing neural networks
- Generate authentic new data

#### VAE (Variational Autoencoder)
- Probabilistic description in latent space

---

## Security & Governance

### Security Concepts

#### Bias
- Unfair prejudice favoring/disfavoring groups

#### Fairness
- Impartial treatment without discrimination

#### Explainability
- Understanding HOW model arrives at predictions
- **Tools**: SHAP, Partial Dependency Plots

#### Interpretability
- Understanding WHAT the model does internally
- How model combines features for predictions

### AI Attacks & Vulnerabilities

#### Prompt Injection
- Ignoring prompt templates
- Persona switches, fake completions
- Rephrasing/obfuscating attacks

#### Poisoning
- Intentional malicious data in training
- Leads to biased/harmful outputs

#### Hijacking
- Influencing outputs via embedded instructions
- Goal: Make model produce attacker-aligned outputs

#### Prompt Leaking
- Unintentional disclosure of prompts/inputs
- Can reveal model workings

#### Jailbreaking
- Circumventing safety measures/constraints
- Crafted prompts to bypass filtering

#### Hallucination
- Incorrect or misleading AI-generated results

### Security Services

#### AWS Artifact
- Audit resource for security/compliance documentation

#### AWS CloudTrail
- User activity and API usage tracking

#### Amazon CloudWatch
- Centralized logging and monitoring

#### AWS Trusted Advisor
- Cost optimization, security, resilience recommendations

#### Amazon Macie
- ML-based sensitive data discovery in S3
- PII identification and compliance

#### AWS PrivateLink
- Private VPC connectivity
- Connect to SageMaker via VPC endpoints

#### Amazon Inspector
- Automated security assessment
- EC2, Lambda, ECR repository scanning

#### AWS Audit Manager
- Automated evidence collection
- Risk and compliance assessment

### Governance Framework

#### Generative AI Security Scoping Matrix
- Complements existing security practices
- Focuses on unique GenAI risks
- Built on well-established security guidelines

#### AWS AI Service Cards
- Enhance transparency in AI services
- Advance responsible AI practices

#### Amazon A2I (Augmented AI)
- Human review systems for ML solutions
- Audit individual predictions
- **Note**: Not for system-level compliance audits

---

## Amazon Nova Models

### Understanding Models (Text Output)

#### Amazon Nova Micro
- **Type**: Text-only
- **Input**: Text
- **Output**: Text
- **Use**: Lowest latency, very low cost

#### Amazon Nova Lite
- **Type**: Multimodal
- **Input**: Text, image, video
- **Output**: Text
- **Use**: Very low cost, lightning fast processing

#### Amazon Nova Pro
- **Type**: Multimodal
- **Input**: Text, image, video
- **Output**: Text
- **Use**: Best combination of accuracy, speed, cost

#### Amazon Nova Premier
- **Type**: Multimodal
- **Input**: Text, image, video
- **Output**: Text
- **Use**: Most capable for complex tasks, model distillation

### Creative Content Generation Models

#### Amazon Nova Canvas
- **Type**: Multimodal
- **Input**: Text, Image
- **Output**: Image
- **Use**: Image generation, supports negative prompting

#### Amazon Nova Reels
- **Type**: Multimodal
- **Input**: Text, Image
- **Output**: Video
- **Use**: Video generation

### Speech-to-Speech Model

#### Amazon Nova Sonic
- **Type**: Speech
- **Input**: Speech
- **Output**: Speech, Text
- **Use**: Real-time, human-like voice conversations

---

## Key Concepts & Definitions

### Core AI/ML Terms

#### Vector
- Ordered list of numbers representing features/attributes
- In GenAI: Represents words, phrases, sentences

#### Embeddings
- Vector representations capturing semantic relationships
- Similar meanings have close vector representations

#### Vector Database
- Collection of data stored as mathematical representations
- Stores structured/unstructured data with vector embeddings

#### Token
- Sequence of characters interpreted as single unit
- Can be words, word parts, punctuation, phrases

#### Context Window
- Number of tokens model can accept in context

#### Latent Space
- Encoded knowledge within LLM
- Represents complex relationships from training data

#### Confusion Matrix
- Table comparing model predictions to actual values
- Summarizes classification model performance

### Advanced Concepts

#### RLHF (Reinforcement Learning from Human Feedback)
- Fine-tuning technique using human feedback
- Aligns models with human values and preferences

#### Shapley Value
- Determines feature contribution to predictions
- Used by SageMaker Clarify for feature attribution

---

*Last Updated: December 2025*
*Exam Code: AIF-C01*
*Exam Duration: 90 minutes*
*Question Format: Multiple choice and multiple response*

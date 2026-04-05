# AWS Certified Machine Learning - Specialty Study Guide

## Table of Contents
1. [Data Engineering](#data-engineering)
2. [Exploratory Data Analysis](#exploratory-data-analysis)
3. [Machine Learning Implementation and Operations](#machine-learning-implementation-and-operations)
4. [Modeling](#modeling)
5. [Exam Experience & Tips](#exam-experience--tips)
6. [Study Resources](#study-resources)

---

## Data Engineering

### Amazon Kinesis
1. **Kinesis Data Firehose** - Positioned for data ingestion and data transformation
2. **Kinesis Data Streams** - Missing data transformation part, can be combined with ETL Streaming jobs in AWS Glue
   - Shard = base throughput unit (1 MB/sec input, 2 MB/sec output, 1000 PUT records/sec)
   - Data Retention Period minimum: 24 hours
3. **Kinesis Data Analytics** - Offers real-time SQL queries, can invoke Lambda for data transformation
4. **Amazon Managed Service for Apache Flink** - Real-time streaming data processing
   - RANDOM_CUT_FOREST function detects anomalies

### Amazon S3 & Storage
5. **S3 to FSx for Lustre** - Offload data for faster startup and training times
6. **S3 Standard to Standard-IA** - Minimum 30 days wait before transition
7. **SageMaker Pipe Mode** - Optimized protobuf recordIO format, does NOT support Apache Parquet

### Other Services
8. **AWS Batch** - NOT a valid destination for S3 Events
9. **Amazon Data Firehose** - Lambda invocation timeout: 5 minutes maximum
10. **Amazon Redshift Streaming Ingestion** - Native integration with Kinesis Data Streams and MSK

---

## Exploratory Data Analysis

### Dimensionality Reduction
1. **Principal Component Analysis (PCA)** - Dimensionality reduction, de-noising, feature extraction
2. **t-SNE (t-Distributed Stochastic Neighbor Embedding)** - Non-linear dimensionality reduction for high-dimensional data

### Data Visualization
3. **Scatter Plots** - Show correlation between variables
4. **Histograms** - Visualize data distribution only, not correlation with hyperparameters

### Data Processing Techniques
5. **Data Augmentation** - Artificially create new training data from existing data
6. **Imputation** - Replace missing data with substituted values
   - **MICE Algorithm** - Multiple Imputations by Chained Equations
7. **Normalization** - Helps when large range differences exist between numeric variables

### Encoding Techniques
8. **One Hot Encoding** - Convert categorical to binary values (0,1)
9. **Label Encoding** - Convert categorical to integer labels (0,1,2,3,4)
10. **Target Encoding** - Replace categorical with probability of target
11. **Tokenization** - Split strings into semantic words (NLP)

### Sampling Techniques
12. **SMOTE** - Synthetic Minority Oversampling Technique for imbalanced datasets

### Evaluation Metrics
13. **AUC (Area Under Curve)** - Binary classification metric (0-1 range)
14. **Accuracy** - Fraction of correct predictions
15. **Precision** - Minimize false positives (TP/(TP+FP))
16. **Recall** - Minimize false negatives (TP/(TP+FN))
17. **False Negative Rate** = FN/(FN+TP)
18. **RMSE** - Root Mean Square Error for regression models

### Overfitting Solutions
19. **Reduce Model Flexibility** - Feature selection, decrease n-grams, increase regularization
20. **Add Artificial Noise** - Increases variations, helps generalization
21. **L1 Regularization** - Not available for SageMaker Object2vec, use Dropout instead

---

## Machine Learning Implementation and Operations

### Amazon SageMaker Core Features
1. **SageMaker Autopilot** - Automated ML with minimal setup, handles class imbalance automatically
2. **SageMaker Neo** - Optimizes models for inference (not training) on cloud/edge devices
3. **SageMaker Debugger** - Analyzes training data (tensors), works with pre-trained models
4. **Production Variants** - Test multiple models behind same endpoint

### Infrastructure & Deployment
5. **VPC Interface Endpoint** - Direct connection to SageMaker API without internet gateway
6. **GPU Training** - Containers must be nvidia-docker compatible
7. **Docker ENTRYPOINT** - Use exec form to receive SIGTERM/SIGKILL signals
8. **Managed Spot Training** - Use EC2 Spot instances, implement checkpointing for interruptions
9. **Inter-container Traffic Encryption** - Increases training time for distributed learning

### Specialized Services
10. **Amazon A2I (Augmented AI)** - Human review workflows for ML predictions
11. **Amazon Polly** - Custom lexicons for pronunciation (XML format)
12. **Amazon Redshift ML** - Create ML models using SQL commands
13. **Amazon Panorama** - On-premises computer vision with low latency
14. **Amazon Transcribe** - Vocabulary filtering and PII redaction
15. **Amazon Personalize** - Real-time personalized recommendations

### Monitoring & Scaling
16. **CloudWatch Metrics** - Send training metrics, create dashboards
17. **Target-tracking Policy** - Use InvocationsPerInstance metric for auto-scaling
18. **Amazon EMR Task Nodes** - Process data without persistent HDFS storage

---

## Modeling

### Unsupervised Learning Algorithms
1. **Latent Dirichlet Allocation (LDA)** - Topic modeling for text corpus
2. **Random Cut Forest (RCF)** - Anomaly detection
3. **K-means** - Clustering (not classification)
4. **Neural Topic Model (NTM)** - Organize documents into topics

### Supervised Learning Algorithms
5. **BlazingText** - Word2vec and text classification implementations
6. **DeepAR** - Time series forecasting with RNNs
7. **DeepAR+** - Enhanced version with weather featurization
8. **CNN-QR** - Convolutional Neural Network Quantile Regression for forecasting
9. **XGBoost** - Regression, classification, ranking (set objective to multi:softmax)
10. **Sequence-to-Sequence** - Input/output token sequences (translation, summarization)
11. **Factorization Machines** - High-dimensional sparse datasets
12. **IP Insights** - Associations between online resources and IP addresses

### Computer Vision
13. **Image Classification** - Multi-label classification from images
14. **Object Detection** - Detect and classify objects in images
15. **Semantic Segmentation** - Pixel-level classification
16. **Amazon Rekognition** - Content moderation for inappropriate content

### Natural Language Processing
17. **Amazon Comprehend** - Custom entity recognition beyond preset types
18. **TF-IDF** - Term Frequency-Inverse Document Frequency for text vectorization

### Recommendation Systems
19. **Collaborative Filtering** - Based on (user, item, rating) tuples
20. **Content-based Filtering** - Based on user's past behaviors/preferences

### Model Evaluation & Optimization
21. **Confusion Matrix** - Visualize multiclass model performance
22. **K-fold Cross-validation** - Split data into k subsets for training/evaluation
23. **Residuals Analysis** - Review prediction errors for regression
24. **Bayesian Optimization** - Sequential hyperparameter tuning (limited parallelism)
25. **Early Stopping** - Prevent overfitting by stopping when metrics don't improve

### Advanced Techniques
26. **Transfer Learning** - Pre-trained weights + random top layer
27. **Dropout** - Prevent overfitting in neural networks
28. **Model Pruning** - Remove weights that don't contribute to training
29. **Logarithmic Scaling** - For hyperparameters spanning multiple orders of magnitude
30. **Inference Pipelines** - Linear sequence of 2-5 containers for preprocessing/postprocessing

### Bias & Fairness
31. **SageMaker Clarify** - Detect bias during data prep and generate explanation reports
32. **SageMaker Data Wrangler** - Generate bias reports
33. **LASSO Regularization** - Highlights multicollinearity through coefficient shrinkage

---

## Exam Experience & Tips

### Key Focus Areas
- **SageMaker Data Wrangler** - Heavily tested (~5 questions)
- **SageMaker Model Monitor & Clarify** - 2-3 questions each
- **Overfitting/Underfitting** - Various scenarios and solutions
- **Kinesis Services** - Data Streams, Firehose, Analytics
- **AWS Glue ETL** - Data transformation workflows

### Exam Strategy
1. **Don't Panic** - Many questions seem difficult initially
2. **Flag and Move** - Don't spend too long on single questions
3. **Process of Elimination** - Often find right answer by eliminating wrong ones
4. **Read Carefully** - Exam tricks with similar-looking words
5. **Know Supervised vs Unsupervised** - Algorithm classifications
6. **Understand Hyperparameters** - For built-in algorithms

### Important Services to Know
- **ML Services**: Textract, Rekognition, Personalize, Comprehend, Polly, Transcribe
- **SageMaker Tools**: Model Monitor, Data Wrangler, Clarify, Debugger, Autopilot
- **AWS Infrastructure**: EMR, Kinesis family, Glue, IoT, DMS, S3, VPC

### Model Evaluation Mastery
- **F1 Score** and its components
- **True/False Positives/Negatives** relationships
- **When to use which metric** (Precision vs Recall scenarios)
- **Overfitting vs Underfitting** indicators and solutions

---

## Study Resources

### Essential Materials
1. **AWS Exam Guide** - Official certification guide
2. **Mike Chambers ML Course** - Comprehensive introduction to ML on AWS
3. **Tutorials Dojo Practice Exams** - Essential for exam preparation
4. **AWS SageMaker Built-in Algorithms Documentation** - Deep dive into each algorithm
5. **AWS SkillBuilder Exam Readiness Course** - Official AWS preparation

### Practice Questions
- **Official AWS Practice Questions** - SkillBuilder platform
- **ExamTopics Question Dumps** - Community-verified answers
- **ChatGPT/Amazon Q** - For concept clarification and additional practice

### Documentation Deep Dives
- **SageMaker Developer Guide** - Complete service documentation
- **AWS ML Services Documentation** - Textract, Rekognition, Comprehend, etc.
- **SageMaker Tools Documentation** - Model Monitor, Debugger, Data Wrangler, Clarify

### Success Tips
- Spend 1-2 hours daily for 4-6 weeks
- Focus on hands-on labs and practical implementation
- Understand service integrations and workflows
- Practice with real AWS console when possible
- Use AI assistants for concept clarification and additional questions

---

*Last Updated: December 2025*
*Exam Duration: 3 hours*
*Passing Score: 750/1000*

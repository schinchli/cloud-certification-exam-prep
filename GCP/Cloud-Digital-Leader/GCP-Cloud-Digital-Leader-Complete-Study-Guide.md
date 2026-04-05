# Google Cloud Platform - Exam Study Notes

### Why Go to The Cloud? The Business Revolution

- Eliminates large upfront costs (CapEx → OpEx)
- Provides speed and agility (minutes vs weeks)
- Focus on products, not hardware management
- Shift from owning depreciating assets to consuming scalable services

### The 5 Pillars of Cloud Value

1. **Agility**: Speed to innovate and respond to change
2. **Scalability**: Grow or shrink resources to meet demand
3. **Flexibility**: Choose right tools for specific needs
4. **Security**: Leverage world-class cloud provider expertise
5. **Cost**: Financial benefit of renting vs owning infrastructure

### Key Terms Defined

- **The Cloud**: Network of data centers providing computing services over internet
- **Cloud-Native**: Applications specifically designed for cloud
- **Data**: Information businesses use to create value and insights
- **Digital Transformation**: Fundamental business change enabled by cloud technology
- **Open Source**: Software with publicly available code fueling cloud innovation

### On-Premises vs Cloud

- **On-premises**: Own and manage physical hardware (slow, expensive)
- **Cloud**: Rent and access resources over internet (fast, flexible)
- **Key shift**: From owning assets to consuming services

## Cloud Infrastructure Models

### Public Cloud

- All infrastructure and data on cloud provider (e.g., Google Cloud)
- No on-premises infrastructure

### Private Cloud

- Cloud environment dedicated to single organization
- Hosted in organization's own data center
- Provides cloud-like benefits (virtualization, self-service)
- Total control over infrastructure

### Hybrid Cloud

- Combines on-premises/private cloud with public cloud
- Keep sensitive data on-premises for compliance
- Use public cloud for scalability and advanced services
- **Use case**: Regulated industries needing data residency

### Multi-cloud

- Uses services from multiple public cloud providers (e.g., Google Cloud + AWS)
- Avoids vendor lock-in
- Leverages best services from each provider
- Improves resilience

## Compute Services

### Containers vs Virtual Machines

- **VMs**: Virtualize hardware, include full guest OS, take minutes to start
- **Containers**: Virtualize OS, share host kernel, start in seconds/milliseconds
- **Portability**: Containers more portable across environments
- **Efficiency**: Containers more lightweight and efficient

### Compute Engine (IaaS)

- **What it is**: Infrastructure-as-a-Service providing virtual machines
- **AWS Equivalent**: Amazon EC2 (Elastic Compute Cloud)
- **Key features**:
  - Full root access and OS control
  - User manages OS patching and security updates
  - Custom machine types with specific vCPU/memory
  - Best for legacy apps with specific OS requirements
- **High availability**: Use Managed Instance Groups (MIG) with Load Balancer for autohealing and autoscaling
- **Use cases**: Legacy applications, custom OS requirements, maximum control

### Google Kubernetes Engine (GKE)

- **What it is**: Managed Kubernetes service for container orchestration
- **AWS Equivalent**: Amazon EKS (Elastic Kubernetes Service)
- **Key features**:
  - Industry standard for complex microservices
  - Declarative deployment and scaling
  - Manages hundreds of interdependent containers
  - Open-source Kubernetes (avoids vendor lock-in)
- **Use cases**: Complex multi-container applications, microservices at scale

### GKE Enterprise (formerly Anthos)

- **What it is**: Unified control plane for Kubernetes across environments
- **AWS Equivalent**: Amazon EKS Anywhere + AWS Outposts (partial equivalent)
- **Key features**:
  - Manage clusters on-premises, Google Cloud, and other clouds
  - Consistent platform across all environments
  - Single management interface
- **Use cases**: Multi-cloud/hybrid Kubernetes management

### Cloud Run

- **What it is**: Serverless platform for stateless containers
- **AWS Equivalent**: AWS Fargate + AWS App Runner
- **Key features**:
  - Fully managed, no cluster provisioning
  - Scales to zero automatically
  - Invoked via HTTP requests
  - Pay only for actual usage (vCPU, memory, requests)
  - Managed HTTPS with TLS certificates
- **Use cases**: Stateless containerized web services, APIs

### Cloud Functions (Cloud Run Functions)

- **What it is**: Function-as-a-Service (FaaS) for event-driven code
- **AWS Equivalent**: AWS Lambda
- **Key features**:
  - Executes short, single-purpose code snippets
  - Triggered by events (Cloud Storage uploads, Pub/Sub messages)
  - Most cost-effective for simple tasks
  - Scales automatically
- **Use cases**: Image processing on upload, event-driven automation, background tasks

### App Engine

- **What it is**: Platform-as-a-Service (PaaS) for web applications
- **AWS Equivalent**: AWS Elastic Beanstalk
- **Standard Environment**:
  - Deploy from source code directly
  - Specific language runtimes (Python, Go, Java, etc.)
  - Scales to zero
  - No custom Docker containers
  - Hermetic, language-specific runtimes
- **Flexible Environment**:
  - Supports custom Docker containers
  - More control over runtime
- **Use cases**: Full web applications with zero server management

### Serverless Computing

- **What it is**: Execution model where cloud provider manages all infrastructure
- **Key benefits**:
  - No server provisioning or management
  - Automatic scaling (including scale to zero)
  - Pay only for actual usage
  - Focus exclusively on code
- **Services**: Cloud Functions, Cloud Run, App Engine
- **Trade-off**: Less control vs ease of use
- **Analogy**: Like staying in a hotel where all infrastructure management is handled for you

### The Three Main Compute Options (With Analogies)

- **Virtual Machine (VM)**: Like a complete, isolated house offering maximum control
  - Service: Compute Engine (GCE)
- **Container**: Like an efficient, isolated apartment sharing building's core infrastructure
  - Service: Google Kubernetes Engine (GKE)
- **Serverless**: Like staying in a hotel with all infrastructure management handled
  - Services: Cloud Run, Cloud Functions, App Engine

### Three Key Concepts for Modern Applications

- **Microservices**: Architecture building applications as set of small, independent services
- **Autoscaling**: Automatically adjusts resources to match user demand
- **Load Balancer**: Acts as traffic cop, distributing requests across running servers

### Bare Metal Solution

- **What it is**: Dedicated physical servers for specialized workloads
- **AWS Equivalent**: AWS Outposts (on-premises) or EC2 Bare Metal Instances
- **Key features**:
  - Non-virtualized, certified hardware
  - Low latency connection to Google Cloud services
  - Runs workloads not certified for virtualization
- **Use cases**: Oracle databases, SAP HANA, specialized enterprise workloads
- **When to choose**: Need certified physical hardware, workload not approved for virtualized environment, migrating from on-premises specialized systems

## Data Processing & Analytics

### BigQuery

- **What it is**: Serverless data warehouse for analytics (OLAP)
- **AWS Equivalent**: Amazon Redshift (managed) or Amazon Athena (serverless)
- **Key features**:
  - Runs fast SQL queries on petabytes of data
  - Separates storage and compute (scale independently)
  - NOT for OLTP workloads
  - Purpose-built for analytical queries
  - Native Google Analytics 4 integration
  - Remote functions (call external APIs like Natural Language API)
  - Saved queries and views for sharing
- **Use cases**: Large-scale data analysis, business intelligence, historical trend analysis, custom Google Analytics analysis
- **When to choose**: Need to analyze large datasets with SQL, want serverless analytics, have structured/semi-structured data

### Dataflow

- **What it is**: Fully managed stream and batch data processing
- **AWS Equivalent**: Amazon Kinesis Data Analytics + AWS Glue
- **Key features**:
  - Transform engine in ETL/ELT pipelines
  - Built on Apache Beam
  - Real-time data transformation and enrichment
- **Use cases**: Data transformation between Pub/Sub and BigQuery, cleaning and enriching streaming data

### Dataproc

- **What it is**: Fully managed Hadoop/Spark service
- **AWS Equivalent**: Amazon EMR (Elastic MapReduce)
- **Key features**:
  - Runs Apache Spark, Apache Flink, Presto
  - Fast, cost-effective
  - Open-source ecosystem compatibility
  - Quick cluster provisioning (90 seconds)
  - Batch processing on clusters
- **Use cases**: Migrate existing Hadoop/Spark workloads, big data processing, parallel batch jobs
- **When to choose**: Have existing Hadoop/Spark jobs, need open-source tools, want managed service vs self-managing on Compute Engine

### Cloud Data Fusion

- **What it is**: Visual ETL/ELT data pipeline builder
- **AWS Equivalent**: AWS Glue Studio (visual ETL)
- **Key features**:
  - Drag-and-drop interface
  - Build and manage data pipelines
  - Based on open-source CDAP
  - No-code/low-code ETL
- **Use cases**: Building data integration pipelines, ETL workflows
- **When to choose**: Need visual pipeline builder, want no-code ETL, data integration projects

### Cloud Scheduler

- **What it is**: Fully managed cron job service
- **AWS Equivalent**: Amazon EventBridge Scheduler (formerly CloudWatch Events)
- **Key features**:
  - Schedule jobs to run at specific times
  - Trigger Cloud Functions, Pub/Sub, HTTP endpoints
  - Cron-like scheduling
- **Use cases**: Scheduled batch jobs, periodic tasks, nightly processing
- **When to choose**: Need to run tasks on schedule, trigger functions periodically

### Cloud Composer

- **What it is**: Managed workflow orchestration service
- **AWS Equivalent**: Amazon MWAA (Managed Workflows for Apache Airflow)
- **Key features**:
  - Based on Apache Airflow
  - Complex workflow orchestration
  - DAG (Directed Acyclic Graph) workflows
- **Use cases**: Complex data pipelines, multi-step workflows
- **When to choose**: Need complex workflow orchestration, have dependencies between tasks

### Pub/Sub

- **What it is**: Asynchronous messaging service
- **AWS Equivalent**: Amazon SNS (Simple Notification Service) + Amazon SQS (Simple Queue Service)
- **Key features**:
  - Decouples publishers and subscribers
  - Reliable message bus for microservices
  - Handles millions of events per hour
- **Use cases**: Event ingestion, microservices communication, IoT data capture

### Looker

- **What it is**: Business intelligence and data visualization platform
- **AWS Equivalent**: Amazon QuickSight
- **Key features**:
  - Self-service BI for non-technical users
  - Interactive dashboards and reports
  - Connects to BigQuery and other data sources (multi-cloud)
  - No SQL knowledge required
  - LookML modeling layer for consistent business logic
  - Centralized data definitions
- **Use cases**: Executive dashboards, data exploration, strategic decision-making, self-service analytics
- **When to choose**: Need BI tool for business users, want consistent data definitions across organization, require self-service reporting

### Data Lake

- **What it is**: Storage repository for massive amounts of raw data in native format
- **Key features**:
  - No predefined schema required
  - Stores structured, semi-structured, and unstructured data
  - Built on Cloud Storage
  - Cost-effective for petabytes of data
- **Use cases**: Storing raw video, audio, social media feeds, IoT data

### The Data Hierarchy

- **Database**: Runs daily operations
  - Relational (SQL): Structured data
  - NoSQL: Flexible needs
- **Data Warehouse**: Historical analysis of structured data (BigQuery)
- **Data Lake**: All types of raw data for future exploration (Cloud Storage)
- **SQL**: Language to communicate with relational databases

### Two Main Forms of Data

- **Structured Data**:
  - Highly organized in predefined format
  - Like spreadsheet with rows and columns
  - Easy for computers to analyze
  - Examples: Relational database tables, CSV files
- **Semi-structured Data**:
  - Has self-describing schema with tags/key-value pairs
  - Not as rigid as relational tables
  - Examples: JSON, XML files
- **Unstructured Data**:
  - No predefined format or data model
  - Like email text or images
  - More complex to analyze but holds enormous value
  - Examples: Audio (MP3), video, images, PDFs, email body

### Redundancy

- **What it is**: Duplicating critical components to provide backup
- **AWS Equivalent**: Multi-AZ deployments, Read Replicas
- **Key features**:
  - Protects against component failure
  - Increases reliability
  - Example: Cloud SQL with standby instance in different zone
- **Use cases**: High availability, fault tolerance
- **When to implement**: Critical systems, production databases

### Cloud Sprawl

- **What it is**: Decentralized, unpredictable cloud spending pattern
- **Problem**: Teams using services without clear budget/oversight
- **Solution**: Implement FinOps practices
- **Characteristics**: Flexible but difficult to track and control
- **Prevention**: Resource quotas, budgets, organization policies

### AI vs ML vs Data Analytics

- **Data Analytics**: Describes the past by analyzing historical data
- **Machine Learning (ML)**: Predicts the future by learning patterns from data
- **Artificial Intelligence (AI)**: Broadest field of creating intelligent systems (ML is key part)

### Streaming vs Batch Data

- **Streaming**: Processed continuously as generated, low latency, real-time insights
  - Services: Pub/Sub, Dataflow
  - Use cases: Fraud detection, IoT monitoring
- **Batch**: Processed in large chunks at intervals (hourly, daily)
  - Services: Dataflow, BigQuery
  - Use cases: Historical analysis, reporting

### Key Components of Streaming Analytics

- **Streaming Analytics**: Process of analyzing data in real-time as it's generated
- **Pub/Sub**: Scalable messaging service to ingest massive data event streams
- **Dataflow**: Powerful processing engine to transform and analyze streaming data on the fly

### Two Main Strategies for Database Modernization

- **"Lift and Shift"**:
  - Fastest approach
  - Move database to similar managed service with minimal changes
  - Prioritizes speed and simplicity
- **"Move and Improve"**:
  - More transformational
  - Migrate to modern cloud-native database
  - Unlock new capabilities
  - Prioritizes long-term innovation

### Data Value Chain Stages

1. **Generate**: Create/collect raw data
2. **Store**: Keep data in repositories (Cloud Storage, databases)
3. **Transform**: Combine, clean, enrich data from multiple sources
4. **Analyze**: Extract insights and create visualizations

### ETL (Extract, Transform, Load)

- **What it is**: Process to move and prepare data
- **Steps**:
  - **Extract**: Get data from source systems
  - **Transform**: Reformat, cleanse, join, convert data
  - **Load**: Put data into destination (data warehouse)
- **Purpose**: Prepare data for analysis, ensure consistency
- **Use cases**: Populate data warehouse, integrate multiple data sources
- **When to use**: Moving data from transactional systems to analytics systems

### Data Governance

- **What it is**: Overall management of data as valuable asset
- **Key aspects**:
  - Maintain data quality, availability, security
  - Define who can access what data
  - Establish policies and processes
  - Ensure data trustworthiness
  - Define retention policies
- **NOT**: Giving everyone full access or deleting all data
- **When to implement**: Handling sensitive data, compliance requirements, multiple data sources

## Database Services

### Cloud SQL

- **What it is**: Fully managed relational database (MySQL, PostgreSQL, SQL Server)
- **AWS Equivalent**: Amazon RDS (Relational Database Service)
- **Key features**:
  - Regional service
  - Automated backups and patching
  - OLTP workloads
  - Direct replacement for on-premises databases
- **Use cases**: WordPress sites, transactional databases, single-region applications

### Cloud Spanner

- **What it is**: Globally distributed, strongly consistent relational database
- **AWS Equivalent**: Amazon Aurora Global Database (partial equivalent, not as globally distributed)
- **Key features**:
  - Horizontal scaling across continents
  - Full SQL and ACID transactions
  - Strong global consistency
  - Combines NoSQL scale with relational integrity
- **Use cases**: Global trading platforms, multiplayer games, applications requiring global consistency

### Cloud Bigtable

- **What it is**: NoSQL wide-column store
- **AWS Equivalent**: Amazon DynamoDB (key-value/document) or Amazon Keyspaces (Cassandra-compatible)
- **Key features**:
  - Sub-10ms latency
  - Massive write throughput
  - Designed for operational workloads
  - NOT relational
- **Use cases**: IoT time-series data, high-throughput operational workloads

### Firestore

- **What it is**: NoSQL document database for mobile/web apps
- **AWS Equivalent**: Amazon DynamoDB + AWS AppSync (for real-time sync)
- **Key features**:
  - Real-time data synchronization
  - Robust offline support
  - Client-side SDK
- **Use cases**: Real-time collaboration apps, mobile applications, offline-first apps

## Storage

### Cloud Storage

- **What it is**: Object storage for unstructured data
- **AWS Equivalent**: Amazon S3 (Simple Storage Service)
- **Key features**:
  - Stores files (images, videos, backups)
  - Durable and highly available
  - Can serve static website content
  - NOT a database
- **Storage Classes** (by access frequency and cost):
  - **Standard**: Frequently accessed ("hot") data, highest cost
  - **Nearline**: Accessed < once/month, lower cost
  - **Coldline**: Accessed < once/quarter, very low cost
  - **Archive**: Accessed < once/year, lowest cost (long-term archival)
- **Use cases**: Media archives, backups, data lakes, static website hosting

## AI/ML Services

### Vertex AI

- **What it is**: Unified AI platform for entire ML lifecycle
- **AWS Equivalent**: Amazon SageMaker
- **Key features**:
  - Data preparation to deployment
  - AutoML and custom model training
  - Model versioning and management
  - MLOps capabilities
  - Collaboration for data scientists, ML engineers, developers
- **Components**:
  - **Vertex AI Workbench**: Managed Jupyter notebook environment, custom Python libraries, integrates with BigQuery/Cloud Storage
  - **Vertex AI Training**: Run custom TensorFlow/PyTorch scripts with full control
- **Use cases**: End-to-end ML workflows, custom model development
- **When to choose**: Need unified MLOps platform, want full ML lifecycle management, require custom model training with control

### AutoML

- **What it is**: Train custom ML models with minimal coding
- **AWS Equivalent**: Amazon SageMaker Autopilot
- **Key features**:
  - Automatically explores model architectures
  - Requires labeled dataset
  - No ML expertise needed
  - High-quality custom models
- **Types**:
  - **AutoML Text Classification**: Categorize text into custom topics
  - **AutoML Vision**: Custom image classification
  - **AutoML Tables**: Structured data predictions
- **Use cases**: Proprietary business processes (fraud detection), unique classification tasks, customer support email categorization
- **When to choose**: Have labeled data, need custom model, lack ML expertise, pre-trained APIs too generic

### Pre-trained APIs

- **Vision API**:
  - Image analysis, labeling, OCR, face detection
  - Safe Search detection for content moderation (adult/violent content)
  - **AWS Equivalent**: Amazon Rekognition
- **Natural Language API**: Entity extraction, sentiment analysis, syntax analysis
  - **AWS Equivalent**: Amazon Comprehend
- **Translation API**: Language translation
  - **AWS Equivalent**: Amazon Translate
- **Speech-to-Text API**: Transcribe audio to text
  - **AWS Equivalent**: Amazon Transcribe
- **Text-to-Speech API**: Convert text to audio
  - **AWS Equivalent**: Amazon Polly
- **Key benefit**: No ML expertise required, ready-to-use
- **Use cases**: Quick implementation of common AI tasks

### Cloud TPU

- **What it is**: Google's custom ML accelerator hardware
- **AWS Equivalent**: AWS Inferentia/Trainium chips (custom ML accelerators)
- **Key features**:
  - Optimized for TensorFlow
  - Significantly faster than GPUs for large models
  - Purpose-built ASIC
- **Use cases**: Large-scale ML model training

### BigQuery ML

- **What it is**: Create ML models on data within BigQuery
- **AWS Equivalent**: Amazon Redshift ML
- **Key features**:
  - Works with structured data in BigQuery
  - SQL-based model creation
- **Use cases**: ML on structured data already in BigQuery

### Machine Learning Core Concepts

- **Primary business value**: Find patterns in data to make predictions and support decision-making at scale
- **Data quality importance**: "Garbage in, garbage out" - model quality depends on training data quality
- **Limitations**:
  - Models are probabilistic, never 100% accurate
  - Requires large amounts of high-quality data
  - Augments human intelligence, doesn't replace oversight
- **Unlocking value from unstructured data**: Analyze audio, video, text that traditional BI tools can't process

### AI vs ML vs Deep Learning

**Artificial Intelligence (AI)**:
- Technology that mimics human intelligence
- Umbrella term including ML and Deep Learning
- Learns through massive amounts of training data
- Solves complex problems across industries
- Excels at pattern recognition and processing large data
- Operates on probability-based decision making
- Requires transparency, fairness, human oversight

**Machine Learning (ML)**:
- Subset of AI focused on learning from data
- Transforms programming by learning patterns vs following rules
- Three main types: Supervised, Unsupervised, Reinforcement Learning
- Data quality and quantity crucial
- Models improve continuously with more data
- Challenges: computation, algorithm selection, explainability

**Deep Learning (DL)**:
- Specialized subset of ML using Neural Networks with multiple layers
- Excels at unstructured data (images, text, sound)
- Automatically discovers features without human guidance
- Requires massive data and computational power
- Powers content generation and NLP
- More complex and harder to interpret than traditional ML
- Architecture inspired by human brain

### The AI/ML Spectrum on Google Cloud

- **Pre-trained APIs**: Fastest, easiest for common use cases
- **AutoML**: Balance of speed and customization, train on your data without code
- **Custom Models**: Maximum control and differentiation, requires ML expertise

### ML Problem Types

- **Classification**: Predict discrete category (spam/not spam, churn/no churn, email topic)
  - Binary: Two categories
  - Multi-class: Multiple categories
- **Regression**: Predict continuous numerical value (house price, temperature, sales forecast)
- **Clustering**: Group similar data without predefined labels (customer segmentation)
- **Anomaly Detection**: Identify outliers or unusual patterns (fraud detection)

### TensorFlow

- **What it is**: Open-source ML platform and library
- **AWS Equivalent**: TensorFlow (same - open source) or AWS-optimized frameworks
- **Key features**:
  - Developed by Google
  - Large community and ecosystem
  - Tools and libraries for building/training models
  - Optimized for Cloud TPUs
- **Use cases**: Custom ML model development, research, production ML systems

## Networking & API Management

### Apigee API Management

- **What it is**: Full-lifecycle API management platform
- **AWS Equivalent**: Amazon API Gateway + AWS AppSync
- **Key features**:
  - Security, rate limits, quotas
  - API analytics and monetization
  - Manage APIs as products
  - Developer portals for partners
  - Create B2B opportunities through APIs
- **Use cases**: Exposing services to external partners, API monetization, sharing data securely

### DNS (Domain Name System)

- **What it is**: Translates domain names to IP addresses
- **Analogy**: "Phonebook of the internet"
- **Function**: Converts human-readable names (www.google.com) to IP addresses (142.250.190.78)

### Cloud Load Balancing

- **What it is**: Distributes traffic across multiple instances
- **AWS Equivalent**: Elastic Load Balancing (ELB) - ALB, NLB, CLB
- **Key features**:
  - Works with Managed Instance Groups
  - Health checks and automatic recovery
  - Increases reliability and availability
  - Prevents single instance from being overwhelmed
- **Use cases**: High availability, traffic distribution

### Cloud CDN

- **What it is**: Content Delivery Network
- **AWS Equivalent**: Amazon CloudFront
- **Key features**:
  - Caches content closer to users
  - Reduces latency
  - Does not manage APIs
- **Use cases**: Faster content delivery globally

### Cloud Armor

- **What it is**: Network security service and Web Application Firewall (WAF)
- **AWS Equivalent**: AWS WAF + AWS Shield
- **Key features**:
  - Works with Cloud Load Balancer
  - DDoS protection
  - Protects against SQL injection and web attacks
  - Application-layer defense
- **Use cases**: Web application security, attack prevention

## Security & Identity

### IAM (Identity and Access Management)

- **AWS Equivalent**: AWS IAM (Identity and Access Management)
- **Principle of Least Privilege**: Grant minimum necessary permissions
- **Best practices**:
  - Grant permissions to groups, not individuals
  - Assign most specific predefined role needed
  - Avoid over-permissioning
- **Predefined Roles**:
  - **Owner**: Full control including billing and deletion
  - **Editor**: Deploy apps, modify resources (no billing/access management)
  - **Viewer**: Read-only access
  - **Browser**: Browse resources without seeing data
  - **Billing Account Viewer**: View billing reports only
- **Use cases**: Access control, permission management

### Encryption

- **Google-managed encryption keys**: Default, Google handles automatically
- **Customer-Supplied Encryption Keys (CSEK)**:
  - Customer provides own key
  - Google doesn't store the key
  - Customer manages and protects key
- **Cloud External Key Manager (EKM)**: Key managed in third-party system
- **Encryption in transit**: Data encrypted while moving over network

### Security Concepts

- **Phishing**: Fraudulent messages to steal credentials (social engineering)
- **Ransomware**: Malicious software blocking access until payment
- **DDoS**: Overwhelming service with traffic from multiple sources
- **Man-in-the-middle**: Secretly relaying/altering communications
- **Data Residency**: Physical location where data is stored
- **Data Sovereignty**: Data subject to laws of citizen's nation, regardless of storage location
- **Google's Private Network**: Traffic between services stays within Google's secure network
- **Encryption at rest**: Protects data on physical storage media; makes stolen drives unreadable
- **Encryption in transit**: Protects data moving over networks

### Zero Trust Security Model

- **Core principle**: "Never trust, always verify"
- **Key features**:
  - No automatic trust for any user/device/network
  - Every request must be authenticated and authorized
  - Assumes threats exist inside and outside network
  - Replaces "castle-and-moat" perimeter security
- **When to choose**: Modern security posture, cloud-native applications, remote workforce

### The New Security Paradigm in the Cloud

- **On-premises**: "Castle-and-moat" approach, strong perimeter focus
- **Cloud**: "Zero Trust" model, no one trusted by default, verify every request
- **Shift**: From sole responsibility to Shared Responsibility Model

### Google's Defense-in-Depth Approach

- **Multi-layered strategy**: If one layer fails, another protects
- **Layers include**:
  - Physical security of data centers
  - Custom security hardware (Titan chip)
  - Automatic encryption by default (at rest and in transit)
- **Key benefit**: Comprehensive protection at multiple levels

### Core Security Concepts

- **Encryption**: Scrambling data to make it unreadable without secret key
- **Authentication**: Verifying who you are (login with password)
- **Authorization**: Determining what you're allowed to do after authentication
- **IAM**: Identity and Access Management for access control

### Two Key Security Products

- **IAM**: Central tool for internal access control, enables Principle of Least Privilege
- **Cloud Armor**: Network security service integrating with Cloud Load Balancing to protect from DDoS
- **Together**: Part of Defense-in-Depth strategy, securing from inside and out

### Two-Step Verification (2SV) / Multi-Factor Authentication (MFA)

- **What it is**: Second authentication factor beyond password
- **Key benefits**:
  - Significantly strengthens account security
  - Prevents unauthorized access even with stolen password
  - Requires "something you have" (phone, security key)
- **Use cases**: Protect user accounts, meet compliance requirements
- **When to choose**: Always - security best practice for all accounts

### Cloud Identity

- **What it is**: Identity and access management for users
- **AWS Equivalent**: AWS IAM Identity Center (formerly AWS SSO) + AWS Directory Service
- **Key features**:
  - Manage user accounts centrally
  - Integrate with existing identity systems
  - Enforce 2SV policies
- **Security actions**:
  - Suspend/delete accounts immediately when employee leaves
  - Revokes all access tied to identity
- **When to choose**: Need centralized user management, integrate with existing directory

### CIA Triad

- **Confidentiality**: Data protected from unauthorized access (enforced by encryption, IAM)
- **Integrity**: Data accurate and not improperly modified
- **Availability**: Data and services accessible when needed

### Defense-in-Depth

- **Concept**: Layered security controls
- **Google's responsibility**: Physical security, hardware security, network encryption
- **Customer's responsibility**: IAM configuration, data security, user access management

### Security Command Center

- **What it is**: Centralized security and risk management platform
- **AWS Equivalent**: AWS Security Hub
- **Key features**:
  - Provides visibility and insights
  - Security Health Analytics (scans for misconfigurations)
  - Identifies publicly accessible storage buckets
  - Search IAM policy findings across organization
  - Does not actively block attacks (use Cloud Armor for that)
- **Use cases**: Security monitoring, risk assessment, finding overly permissive roles
- **When to choose**: Need centralized security dashboard, want to identify misconfigurations, audit IAM roles across projects

### Organization Policy Service

- **What it is**: Centralized control over cloud resources
- **AWS Equivalent**: AWS Organizations + Service Control Policies (SCPs)
- **Key features**:
  - Set constraints on which services can be used
  - Enforce security and governance standards
  - Restrict non-approved services
  - Programmatic control over organization
- **Use cases**: Prevent use of insecure services, enforce compliance policies
- **When to choose**: Need to restrict which GCP services can be enabled, enforce organizational standards

### Cloud Audit Logs

- **What it is**: Automatic logging of API calls and access
- **AWS Equivalent**: AWS CloudTrail
- **Key features**:
  - Part of Cloud Logging service
  - Admin Activity logs (who did what)
  - Data Access logs (read/write to resources)
  - Essential for auditing and compliance
  - Records access to BigQuery datasets
- **Use cases**: Audit trails, compliance reporting, security investigations
- **When to choose**: Need to track who accessed what data, compliance requirements for logging

### Cloud Data Loss Prevention (DLP)

- **What it is**: Service for discovering and protecting sensitive data
- **AWS Equivalent**: Amazon Macie
- **Key features**:
  - Data de-identification (masking, tokenization)
  - PII detection and removal
  - Automated data protection
- **Use cases**: Remove PII from datasets, comply with privacy regulations
- **When to choose**: Need to anonymize data, handle PII, meet privacy requirements

### Cloud Key Management Service (KMS)

- **What it is**: Manages cryptographic keys for encryption
- **AWS Equivalent**: AWS KMS (Key Management Service)
- **Use cases**: Key management, encryption key rotation

### Compliance Reports Manager

- **What it is**: Self-service portal for compliance documentation
- **AWS Equivalent**: AWS Artifact
- **Key features**:
  - On-demand access to third-party audit reports
  - Certifications (ISO 27001, SOC 2/3, PCI DSS)
  - Proves Google Cloud infrastructure compliance
  - Does NOT audit customer's projects
- **Use cases**: Provide compliance evidence to auditors, meet regulatory requirements
- **When to choose**: Need to prove cloud provider compliance, regulatory audit requirements

### VPC Firewall Rules

- **What it is**: Network access control for VMs
- **AWS Equivalent**: AWS Security Groups + Network ACLs
- **Key features**:
  - Allow or deny traffic based on configuration
  - Control ingress (incoming) and egress (outgoing) traffic
  - Based on IP addresses, ports, protocols
  - Priority-based rule evaluation
- **Use cases**: Prevent VM from accessing internet, restrict network access, security isolation
- **When to choose**: Need to control network traffic, isolate resources, enforce network security policies

### Artifact Registry

- **What it is**: Secure storage for container images and build artifacts
- **AWS Equivalent**: Amazon ECR (Elastic Container Registry)
- **Key features**:
  - Docker V2 API support
  - Vulnerability scanning
  - Integrates with Cloud Build and GKE
  - Evolution of Container Registry
- **Use cases**: Store container images for CI/CD, manage build artifacts
- **When to choose**: Need container registry, want vulnerability scanning, building containerized applications

## Resource Management

### Geographic Organization

- **Region**: Independent geographic area (e.g., us-central1, europe-west1)
  - Multiple zones within each region
  - Used for disaster recovery
- **Zone**: Isolated location within a region (e.g., us-central1-a)
  - Protects against single data center failure
  - Deploy across multiple zones for high availability
- **Best practice**: Multi-zone deployment within region for HA

### Resource Hierarchy

- **Organization** → **Folders** → **Projects** → **Resources**
- **Folders**: Group projects, apply policies hierarchically
- **Use cases**: Separate dev/prod billing, apply IAM policies to departments

### Resource Quotas

- **What it is**: Hard limits on resource creation
- **AWS Equivalent**: AWS Service Quotas (formerly Service Limits)
- **Key features**:
  - Prevents unforeseen usage spikes
  - Can limit number of VMs, VPCs, etc.
  - NOT the same as billing budgets (which only alert)
- **Use cases**: Prevent uncontrolled spending, enforce resource limits

### Cloud Billing Budgets

- **What it is**: Send alerts when costs exceed thresholds
- **Key limitation**: Does NOT block resource creation

## Operations & Monitoring

### SRE (Site Reliability Engineering)

- **SLI (Service Level Indicator)**: Quantitative measure of service level (e.g., latency, uptime)
- **SLO (Service Level Objective)**: Target value for SLI (e.g., latency < 300ms, 99.9% uptime)
- **SLA (Service Level Agreement)**: Contract with consequences if SLO not met (e.g., billing credits)
- **Error Budget**: Allowed downtime (100% - SLO)
- **Key principle**: Balance reliability with innovation
- **Use of error budget**: Take calculated risks, release new features
- **Culture**: Blameless postmortems, no punishment for errors

### Cloud Monitoring

- **What it is**: Observes metrics and logs
- **AWS Equivalent**: Amazon CloudWatch
- **Key features**:
  - Tracks performance and health
  - CloudWatch metrics for EC2 and RDS
  - NOT for setting resource limits (use Resource Quotas)
  - Custom dashboards for visualizing metrics
  - Uptime checks for service availability
  - Alerting policies for threshold notifications
- **Business value**: Proactive issue identification, visibility into performance, resolve issues before user impact
- **Use cases**: Performance monitoring, troubleshooting, creating operational dashboards
- **When to choose**: Need to track application health, want alerts on performance degradation, require operational visibility

### Cloud Logging

- **What it is**: Aggregates log data from applications and services
- **AWS Equivalent**: Amazon CloudWatch Logs
- **Key features**:
  - Centralized log collection
  - Search and filter capabilities
  - Text-based event records
  - Query logs by time, severity, text content
- **Use cases**: Analysis, troubleshooting, auditing, CI/CD pipeline debugging
- **When to choose**: Need to search application logs, troubleshoot errors, review detailed event records

### Cloud Trace

- **What it is**: Distributed tracing system for latency analysis
- **AWS Equivalent**: AWS X-Ray
- **Key features**:
  - Follows requests through services
  - Diagnoses latency issues
  - Performance bottleneck identification
- **Use cases**: Microservices debugging, latency troubleshooting

### Cloud Profiler

- **What it is**: Continuous profiling for application performance
- **AWS Equivalent**: AWS CodeGuru Profiler
- **Key features**:
  - Analyzes code-level performance
  - Identifies inefficient functions
  - CPU and memory profiling
- **Use cases**: Performance optimization, finding resource-intensive code

### The Four Golden Signals (SRE Monitoring)

- **What it is**: Most important metrics for monitoring user-facing systems
- **AWS Equivalent**: Similar monitoring principles in AWS CloudWatch
- **The Four Signals**:
  1. **Latency**: Time to serve a request (response time)
  2. **Traffic**: Amount of demand on system (requests per second)
  3. **Errors**: Rate of failing requests (error codes)
  4. **Saturation**: How "full" system is (CPU/memory utilization)
- **Use cases**: Service health monitoring, incident investigation
- **When to monitor**: All production user-facing services

### Cloud Billing Reports

- **What it is**: Detailed visual breakdowns of costs
- **AWS Equivalent**: AWS Cost Explorer
- **Key features**:
  - Filter and group by project, service, time range
  - Understand spending patterns
  - Identify optimization areas
- **Use cases**: Cost analysis, budget tracking

### Cloud Billing Budgets

- **What it is**: Send alerts when costs exceed thresholds
- **AWS Equivalent**: AWS Budgets
- **Key features**:
  - Set thresholds (e.g., 90%, 100% of budget)
  - Automatic email notifications
  - Proactive cost control
- **Key limitation**: Does NOT block resource creation

### Pricing Calculator

- **What it is**: Estimate future costs before deployment
- **AWS Equivalent**: AWS Pricing Calculator
- **NOT for**: Analyzing past/current spending (use Billing Reports)

### Google Cloud Customer Care (Support Tiers)

- **AWS Equivalent**: AWS Support Plans (Basic, Developer, Business, Enterprise)
- **Basic Support**:
  - Billing and payments support only
  - No technical support
  - No guaranteed response times
- **Standard Support**:
  - 4-hour response for P1 (urgent) cases
  - Technical support included
- **Enhanced Support**:
  - 1-hour response for P1 cases
  - Faster technical support
- **Premium Support**:
  - 15-minute response for P1 cases
  - Technical Account Manager (TAM)
  - Mission-critical workloads
  - 24/7 coverage
- **Support case lifecycle**:
  - Stages: Creation → Assignment → Investigation → Resolution → Closure
  - Ongoing communication, add information to existing case
  - Track in Console
- **Priority levels**: P1 (urgent) to P4 (low priority)
- **When to choose each tier**: Based on business criticality and required response times

### How Do You Get Help on Google Cloud?

- **Customer Care**: Helps accelerate cloud adoption with expert guidance
- **Plans**: Basic to Premium
- **Support case lifecycle**: Clear stages from creation to closure
- **Priority assignment**: P1-P4 dictates urgency and response time

### Google's Commitment to Sustainability

- **Industry's cleanest cloud**: Long-standing carbon neutral commitment
- **Goal**: 24/7 carbon-free energy
- **By migrating to Google Cloud**:
  - Meet ESG reporting requirements
  - Reduce carbon footprint
- **Tools**: Carbon Footprint provides data and recommendations to measure and optimize environmental impact
- **Business benefit**: Reducing environmental impact by running on cleanest cloud

### DevOps

- **What it is**: Combines development and operations
- **Cultural philosophy**: Breaking down silos to increase speed and collaboration
- **Key benefits**:
  - Breaks down silos
  - Faster release cycles
  - Continuous delivery
  - Automated deployment
- **Five key objectives**:
  1. Reduce organizational silos
  2. Accept failure as normal (design for resilience)
  3. Implement gradual, frequent changes
  4. Leverage tooling and automation
  5. Measure everything
- **Contrast with**: Waterfall (sequential phases), ITIL (process-heavy)
- **When to adopt**: Want faster deployments, need better collaboration, aim to reduce manual processes

### Two Key Concepts for Operational Excellence

- **DevOps**: Cultural philosophy of breaking down silos for speed and collaboration
- **SRE (Site Reliability Engineering)**: Specific engineering discipline implementing DevOps using data and automation
- **SRE relies on**: SLIs, SLOs, MTTR, powered by Cloud Monitoring and Logging

### Two Critical Reliability Strategies

- **High Availability (HA)**:
  - Proactive strategy
  - Uses multiple zones and Load Balancing
  - Prevents downtime from small, localized failures
- **Disaster Recovery (DR)**:
  - Reactive strategy
  - Recovers from large-scale regional disasters
  - Defined by RTO (Recovery Time Objective) and RPO (Recovery Point Objective)
- **Modern approach**: Automated failover and scaling for both HA and DR

### SecOps

- **What it is**: Security integrated throughout development lifecycle
- **Key principle**: "Shift security left"
- **Approach**: Automated security scanning in CI/CD pipeline
- **Evolution of**: DevOps culture applied to security

### Infrastructure as Code (IaC)

- **What it is**: Define infrastructure in configuration files (e.g., Terraform)
- **Key benefits**:
  - Faster deployments
  - Reduces human error
  - Version-controlled
  - Reusable and consistent
- **Contrast with**: Manual server configuration
- **Use cases**: Automated infrastructure deployment

### FinOps (Cloud Financial Operations)

- **What it is**: Cultural practice for cloud financial accountability
- **Key principles**:
  - Align technology spending with business value
  - Collaboration between finance, technology, business teams
  - Predictability and control over cloud costs
  - Maximize value, not just minimize cost
- **Benefits**: Cost optimization, spending visibility, informed decision-making
- **When to adopt**: Unpredictable cloud spending, need cost accountability, want to optimize cloud investments

## Financial Concepts

### CapEx vs OpEx

- **CapEx (Capital Expenditure)**:
  - Large upfront investment in physical assets (servers, data center)
  - On-premises model
  - Fixed costs regardless of usage
- **OpEx (Operational Expenditure)**:
  - Pay-as-you-go recurring costs
  - Cloud model
  - Costs scale with usage
- **Cloud benefit**: Shifts from CapEx to OpEx, ideal for limited upfront capital

### Total Cost of Ownership (TCO)

- **What it is**: Comprehensive assessment of all costs
- **On-premises TCO includes**:
  - Hardware purchase
  - Data center space (real estate)
  - Power and cooling
  - IT staff for maintenance
  - Software licenses
- **Cloud TCO**: Shifts many costs to provider
- **NOT included**: Marketing budget, all employee salaries

### Elasticity and Scalability

- **Elasticity**: Resources automatically increase/decrease based on demand
- **Scalability**: Ability to handle increased load
- **Cloud benefit**: Handle traffic surges without crashes, pay only for what you use
- **Contrast with on-premises**: Fixed capacity, overprovisioning for peak loads

## Migration Strategies

### Rehost (Lift and Shift)

- Move application as-is to cloud VMs
- No code changes

### Replatform (Move and Improve)

- Optimize during migration
- Example: Self-managed DB → Cloud SQL
- Take advantage of managed services

### Reimagine (Refactor)

- Complete re-architecture
- Build cloud-native applications

### Retire

- Decommission applications

## Cloud Transformation Pillars & Benefits

### Business Transformation Benefits

1. **Intelligence**:
   - AI/ML integrated into data products (BigQuery ML)
   - Democratizes AI for non-specialists
   - Extract insights from unstructured data
2. **Freedom**:
   - Open-source technologies (Kubernetes, TensorFlow)
   - Avoid vendor lock-in
   - Portability across environments
3. **Sustainability**:
   - 100% renewable energy matching since 2017
   - Goal: 24/7 carbon-free energy by 2030
   - Carbon-neutral cloud operations
4. **Collaboration**:
   - Google Workspace tools
   - Real-time document editing
   - Video conferencing

### Transformation Pillars

### 1. Infrastructure Modernization

- Migrate to cloud compute and storage
- Use managed services

### 2. Data Democratization

- Empower users with data access
- Self-service analytics (Looker)
- Remove data gatekeepers

### 3. People Connections

- Collaboration tools (Google Workspace)
- Real-time document editing
- Video conferencing
- Reduce travel costs

### 4. Trusted Transactions

- Secure platforms for commerce
- Transaction security

### Key Business Concepts

- **Agility**: Ability to rapidly develop, test, and launch features; respond quickly to market changes
- **Digital Transformation Risk**: Losing competitiveness and market relevance due to lack of agility
- **Workload**: Specific set of applications, programs, or data requiring computing resources
- **Primary transformation driver**: Pressure from agile competitors and changing customer expectations
- **Fundamental mindset shift**: View technology as strategic enabler for innovation, not just cost center

### Google Cloud Network Benefits

- **Global private fiber network**:
  - High speed, low latency
  - Enhanced security (traffic stays off public internet)
  - Improves application performance
  - Differentiator from competitors
- **When it matters**: Global applications, latency-sensitive workloads, security-conscious organizations

## Cloud-Native Architecture

### Microservices

- **What it is**: Application built as suite of small, modular services
- **Key characteristics**:
  - Each service handles specific business function
  - Loosely coupled and independently deployable
  - Communicates via well-defined interfaces (HTTP APIs)
  - Runs own process
- **Benefits**: Easier to scale, test, and maintain
- **Contrast with**: Monolithic (single indivisible unit)

### Characteristics

- Microservices architecture
- Containerized applications
- Managed by Kubernetes
- Uses managed cloud services (Pub/Sub, Cloud SQL)
- Designed for cloud scalability and resilience

### Key Concepts

- **Autoscaling**: Automatically add/remove resources based on load
- **Serverless**: No infrastructure management
- **Latency**: Time delay for data travel (critical for gaming, real-time apps)

## Responsible AI

### Key Principles

- **Explainability**: Understand and articulate model decisions
- **Critical for**: Regulated industries (finance, healthcare)
- **Use case**: Loan approvals requiring clear reasoning

### AI Risks and Responsible Use

- **Bias amplification**: Models trained on biased data perpetuate discrimination
- **Example**: Hiring models reflecting historical biases leading to unfair practices
- **Mitigation**: Audit training data, test for fairness, diverse datasets
- **Business impact**: Legal liability, reputational damage, ethical concerns
- **When to be cautious**: High-stakes decisions (hiring, lending, healthcare), using historical data

### ML Business Value Examples

- **Improve customer experience**: Personalized recommendations, better engagement
- **Scale business decisions**: Automate predictions at scale
- **Unlock unstructured data**: Extract insights from audio, video, text
- **Predictive analytics**: Forecast demand, identify churn, predict outcomes

## Application Integration

### API (Application Programming Interface)

- **What it is**: Secure "front door" to a service
- **Key benefits**:
  - Expose specific data/functions without revealing internal systems
  - Stable, well-documented integration point
  - Secure alternative to direct database access
  - Enable partner integrations
- **Use cases**: Partner integrations, inventory systems, B2B data sharing
- **When to use**: Need to expose functionality to external parties, want controlled access to systems

## Shared Responsibility Model

### Always Customer Responsibility (All Service Models)

- Security of own data
- User access management (IAM)
- Data classification
- Appropriate data use

### Varies by Service Model

| Responsibility          | IaaS     | PaaS     | SaaS     |
| ----------------------- | -------- | -------- | -------- |
| OS patching             | Customer | Provider | Provider |
| Network/firewall config | Customer | Customer | Provider |
| Application management  | Customer | Customer | Provider |


### Always Provider Responsibility

- Physical data center security
- Hardware security
- Network infrastructure
- Underlying platform security

## Service Models

### Infrastructure as a Service (IaaS)

- **What it is**: Provider manages physical infrastructure
- **Customer manages**: OS, middleware, runtime, applications, data
- **Example**: Compute Engine
- **Trade-off**: Maximum control, more management responsibility

### Platform as a Service (PaaS)

- **What it is**: Provider manages infrastructure, OS, runtime
- **Customer manages**: Applications and data
- **Example**: App Engine
- **Trade-off**: Less control, easier to use

### Software as a Service (SaaS)

- **What it is**: Complete ready-to-use application
- **Customer manages**: Just uses the software
- **Example**: Google Workspace (Gmail, Docs, Meet)
- **Trade-off**: Minimal control, no deployment needed

### Control vs Ease of Use

- **More control** (IaaS) → **Less control** (SaaS)
- **More management** (IaaS) → **Less management** (SaaS)
- **More flexibility** (IaaS) → **Less flexibility** (SaaS)

## Support Best Practices

### Recommended Approach

1. Search official documentation first
2. Check public issue trackers
3. Consult community forums
4. Open support case if needed

### Priority Levels

- **P1 (Urgent)**: Critical production-impacting issues only
- **Non-critical questions**: Use documentation and community resources

## Key Comparisons

### OLTP vs OLAP

- **OLTP** (Online Transaction Processing): High-frequency reads/writes, low latency
  - Services: Cloud SQL, Cloud Spanner, Firestore
- **OLAP** (Online Analytical Processing): Large-scale analytical queries
  - Services: BigQuery

### Compute Service Selection

| Need                                | Service         |
| ----------------------------------- | --------------- |
| Maximum control, custom OS          | Compute Engine  |
| Complex container orchestration     | GKE             |
| Stateless container, HTTP-triggered | Cloud Run       |
| Event-driven function               | Cloud Functions |
| Source code deployment, PaaS        | App Engine      |


### Database Selection

| Need                         | Service        |
| ---------------------------- | -------------- |
| Regional relational DB       | Cloud SQL      |
| Global relational DB         | Cloud Spanner  |
| High-throughput NoSQL        | Cloud Bigtable |
| Mobile/web with offline sync | Firestore      |
| Analytics warehouse          | BigQuery       |


### AI/ML Service Selection

| Need                                    | Service         |
| --------------------------------------- | --------------- |
| Quick common task (translation, vision) | Pre-trained API |
| Custom model, competitive advantage     | Vertex AI       |
| ML on BigQuery data                     | BigQuery ML     |
| Fastest TensorFlow training             | Cloud TPU       |


## Service Selection Decision Matrix

### Compute: When to Choose What

| Scenario                                                 | Choose              | Why                                        |
| -------------------------------------------------------- | ------------------- | ------------------------------------------ |
| Need maximum control, custom OS, specific configurations | Compute Engine      | IaaS with full root access                 |
| Complex microservices with hundreds of containers        | GKE                 | Industry-standard Kubernetes orchestration |
| Multi-cloud/hybrid Kubernetes management                 | GKE Enterprise      | Unified control plane across environments  |
| Stateless container, HTTP-triggered, scale to zero       | Cloud Run           | Serverless containers, pay per use         |
| Event-driven function (file upload, Pub/Sub message)     | Cloud Functions     | FaaS, simplest serverless option           |
| Deploy source code, zero server management               | App Engine          | PaaS, automatic scaling                    |
| Oracle database, SAP HANA, certified hardware required   | Bare Metal Solution | Non-virtualized physical servers           |


### Database: When to Choose What

| Scenario                                                  | Choose         | Why                                      |
| --------------------------------------------------------- | -------------- | ---------------------------------------- |
| Regional relational DB, WordPress, transactional          | Cloud SQL      | Managed MySQL/PostgreSQL/SQL Server      |
| Global relational DB, strong consistency, millions of TPS | Cloud Spanner  | Horizontally scalable, ACID transactions |
| IoT time-series, sub-10ms latency, massive writes         | Cloud Bigtable | NoSQL wide-column, operational workloads |
| Mobile/web app, real-time sync, offline support           | Firestore      | NoSQL document DB with client SDKs       |
| Analyze petabytes with SQL, data warehouse                | BigQuery       | Serverless OLAP, analytics               |


### Data Processing: When to Choose What

| Scenario                                               | Choose                    | Why                                |
| ------------------------------------------------------ | ------------------------- | ---------------------------------- |
| Existing Hadoop/Spark workloads to migrate             | Dataproc                  | Managed Hadoop/Spark ecosystem     |
| Real-time data transformation, ETL/ELT pipelines       | Dataflow                  | Stream and batch processing        |
| Ingest real-time event streams, decouple microservices | Pub/Sub                   | Asynchronous messaging             |
| Self-service BI, dashboards for business users         | Looker                    | Visualization with LookML modeling |
| Store petabytes of raw unstructured data               | Cloud Storage (Data Lake) | Object storage, no schema required |


### AI/ML: When to Choose What

| Scenario                                                 | Choose                     | Why                            |
| -------------------------------------------------------- | -------------------------- | ------------------------------ |
| Translate text, no ML expertise                          | Cloud Translation API      | Pre-trained, ready to use      |
| Transcribe audio to text                                 | Speech-to-Text API         | Pre-trained speech recognition |
| Analyze images, detect objects, OCR                      | Vision AI API              | Pre-trained image analysis     |
| Extract entities, sentiment from text                    | Natural Language API       | Pre-trained NLP                |
| Moderate content for inappropriate images                | Vision AI Safe Search      | Pre-trained content moderation |
| Categorize text into custom topics, have labeled data    | AutoML Text Classification | Custom model, no ML expertise  |
| Custom image classification, have labeled data           | AutoML Vision              | Custom model, minimal coding   |
| Full ML lifecycle, collaboration, MLOps                  | Vertex AI                  | Unified platform, end-to-end   |
| Jupyter notebooks, custom Python libraries               | Vertex AI Workbench        | Managed notebook environment   |
| Full control over model architecture, TensorFlow/PyTorch | Vertex AI Training         | Custom training scripts        |
| ML on structured data already in BigQuery                | BigQuery ML                | SQL-based model creation       |
| Fastest training for large TensorFlow models             | Cloud TPU                  | Google's custom ML hardware    |


### Security: When to Choose What

| Scenario                                               | Choose                      | Why                            |
| ------------------------------------------------------ | --------------------------- | ------------------------------ |
| Centralized security dashboard, find misconfigurations | Security Command Center     | Visibility and insights        |
| Restrict which GCP services can be used                | Organization Policy Service | Enforce governance standards   |
| Audit who accessed what data                           | Cloud Audit Logs            | Automatic API call logging     |
| Protect web app from DDoS, SQL injection               | Cloud Armor                 | WAF and DDoS protection        |
| Remove PII from datasets                               | Cloud DLP                   | Data de-identification         |
| Manage encryption keys                                 | Cloud KMS                   | Cryptographic key management   |
| Prove cloud provider compliance to auditors            | Compliance Reports Manager  | Third-party audit reports      |
| Control VM network access                              | VPC Firewall Rules          | Allow/deny traffic rules       |
| Store container images securely                        | Artifact Registry           | Vulnerability scanning         |
| Centralized user management                            | Cloud Identity              | Identity and access management |


### Operations: When to Choose What

| Scenario                                           | Choose                | Why                            |
| -------------------------------------------------- | --------------------- | ------------------------------ |
| Track application performance, create dashboards   | Cloud Monitoring      | Metrics, alerts, visualization |
| Analyze application logs, troubleshoot errors      | Cloud Logging         | Log aggregation and analysis   |
| Understand cloud spending by project/service       | Cloud Billing Reports | Cost breakdown and analysis    |
| Get alerts when spending exceeds threshold         | Cloud Billing Budgets | Proactive cost notifications   |
| Estimate future costs before deployment            | Pricing Calculator    | Cost estimation tool           |
| Mission-critical workload, need 15-min P1 response | Premium Support       | Highest support tier with TAM  |


### Storage: When to Choose What

| Scenario                                             | Choose                   | Why                      |
| ---------------------------------------------------- | ------------------------ | ------------------------ |
| Frequently accessed files, media, backups            | Cloud Storage (Standard) | Hot data, highest cost   |
| Accessed less than once per month                    | Cloud Storage (Nearline) | Warm data, lower cost    |
| Accessed less than once per quarter                  | Cloud Storage (Coldline) | Cool data, very low cost |
| Long-term archival, accessed less than once per year | Cloud Storage (Archive)  | Cold data, lowest cost   |


### Integration: When to Choose What

| Scenario                                             | Choose                | Why                              |
| ---------------------------------------------------- | --------------------- | -------------------------------- |
| Expose APIs to partners, need rate limits, analytics | Apigee API Management | Full-lifecycle API management    |
| Distribute traffic across multiple VMs               | Cloud Load Balancing  | High availability, health checks |
| Cache content closer to users globally               | Cloud CDN             | Reduce latency                   |


### Key Decision Factors

**Control vs Ease of Use**
- More control needed → IaaS (Compute Engine)
- Balance → PaaS (App Engine, GKE)
- Least management → Serverless (Cloud Functions, Cloud Run)

**OLTP vs OLAP**
- Transactional (frequent reads/writes) → Cloud SQL, Cloud Spanner, Firestore
- Analytical (complex queries, large datasets) → BigQuery

**Pre-trained vs Custom ML**
- Common task, no expertise → Pre-trained API
- Custom task, have labeled data, no expertise → AutoML
- Custom task, need full control → Vertex AI Training

**Real-time vs Batch**
- Real-time streaming → Pub/Sub + Dataflow
- Batch processing → Dataflow, Dataproc
- Both → Dataflow (unified stream and batch)

**Regional vs Global**
- Single region → Cloud SQL
- Global with strong consistency → Cloud Spanner
- Global scale, eventual consistency → Cloud Bigtable

## Additional Exam Concepts from Practice Questions

### Managed Instance Groups (MIG)

- **What it is**: Group of identical VMs managed as a single entity
- **AWS Equivalent**: Auto Scaling Groups (ASG)
- **Key features**:
  - Autoscaling: Automatically adds/removes VMs based on metrics (CPU, requests)
  - Load balancing: Distributes traffic (but doesn't add instances)
  - Autohealing: Recreates failed instances
  - Live migration: Moves VMs between hosts for maintenance
- **Use cases**: Handle traffic spikes, high availability, automatic scaling
- **When to choose**: Need automatic scaling based on demand, want managed VM groups

### Multi-Zone Deployment

- **What it protects against**: Single data center (zone) failure
- **What it doesn't protect against**: Entire region failure
- **For region failure protection**: Deploy to multiple regions
- **Key benefit**: High availability within a region

### Cloud Marketplace

- **What it is**: Pre-configured software packages and application stacks
- **AWS Equivalent**: AWS Marketplace
- **Key features**:
  - One-click deployment
  - Pre-configured, tested solutions
  - Third-party vendor offerings
  - Common stacks (LAMP, etc.)
- **Use cases**: Quick deployment, avoid manual configuration, ensure consistency
- **When to choose**: Need pre-approved application stacks, want rapid deployment

### Admin Activity Logs (Cloud Audit Logs)

- **What it is**: Logs for administrative changes to resources
- **AWS Equivalent**: AWS CloudTrail (Management Events)
- **Key features**:
  - Enabled by default
  - Records configuration/metadata changes
  - Tracks VM creation, firewall changes, etc.
- **Other log types**:
  - Data Access Logs: Read/write operations on data
  - System Event Logs: Google Cloud system events
  - Policy Denied Logs: Access denied due to policy violations
- **Use cases**: Audit administrative changes, compliance, security investigations

### Cloud External Key Manager (EKM)

- **What it is**: Use encryption keys managed in third-party external systems
- **AWS Equivalent**: AWS CloudHSM (partial equivalent)
- **Key features**:
  - Keys stored outside Google infrastructure
  - Customer has ultimate control
  - Google requests key for each operation
  - Customer can revoke access anytime
- **Comparison with other encryption options**:
  - Google-managed: Google controls keys
  - CMEK: Customer controls keys in Cloud KMS
  - EKM: Customer controls keys in external system
- **When to choose**: Need keys outside Google infrastructure, regulatory requirements, maximum control

### BigQuery Pricing Models

- **On-demand pricing**:
  - Pay per query based on data processed
  - Best for: Infrequent, unpredictable queries
  - Cost-effective for low query volumes
- **Flat-rate pricing**:
  - Purchase dedicated query capacity (slots)
  - Best for: High, predictable query volumes
  - Fixed monthly cost
- **Storage pricing**: Cost for storing data
- **Streaming insert pricing**: Cost for streaming data into BigQuery

### Batch Processing

- **What it is**: Running high-volume jobs on finite datasets in groups
- **AWS Equivalent**: AWS Batch + EMR
- **Key features**:
  - Processes large datasets at once
  - Can run in parallel on clusters
  - Scheduled or periodic execution
- **Contrast with**:
  - Streaming: Continuous, real-time processing
  - Transactional: Many small, frequent operations
- **Service**: Dataproc (for Hadoop/Spark batch jobs)

### SAP on Google Cloud

- **What it is**: Certified infrastructure for SAP workloads
- **AWS Equivalent**: SAP on AWS
- **Key features**:
  - SAP-certified VMs and Bare Metal
  - Google Cloud Agent for SAP
  - Automated deployment and monitoring
  - Supports SAP HANA
- **When to choose**: Migrating SAP workloads, need certified infrastructure

### Colocation

- **What it is**: Renting space in data center to house own physical servers
- **Contrast with**:
  - On-premises: Own data center
  - IaaS: Virtual machines in cloud
  - Serverless: No infrastructure management

### Live Migration

- **What it is**: Moving running VM between physical hosts
- **AWS Equivalent**: Similar to EC2 maintenance events (but AWS typically stops/starts)
- **Key features**:
  - No VM interruption
  - Used for host maintenance
  - Transparent to applications
- **NOT for**: Handling traffic spikes (use autoscaling)

### Data Mart

- **What it is**: Subset of data warehouse for specific business line/team
- **AWS Equivalent**: Subset of Redshift or dedicated Redshift cluster
- **Relationship**: Data Warehouse → Data Mart (focused subset)

### Polyglot Development

- **What it is**: Using multiple programming languages in same application
- **Enabled by**: Microservices architecture
- **Key benefit**: Each service uses best language for its task
- **Communication**: Standard protocols (HTTP, gRPC)

### Reinforcement Learning

- **What it is**: ML where agent learns by taking actions to maximize reward
- **Use cases**: Game playing, robotics, autonomous systems
- **Contrast with**:
  - Supervised: Learn from labeled data
  - Unsupervised: Find patterns without labels

### Key Decision Scenarios

**When to use Serverless (Cloud Run/Functions)**:
- Stateless applications
- Pay only when handling requests
- Scale to zero requirement
- No infrastructure management desired

**When to use GKE**:
- Need fine-grained control over cluster
- Complex microservices orchestration
- Custom networking requirements
- Baseline cost acceptable (nodes always running)

**When to use Compute Engine**:
- Lift and shift migrations
- Need full OS control
- Legacy applications
- Specific OS/software requirements

**When to use Cloud Bigtable**:
- Extremely low latency required (sub-10ms)
- Massive scale (petabytes)
- Simple query patterns (key-value lookups)
- Gaming, IoT, time-series data

**When to use BigQuery**:
- Complex analytical queries
- Large-scale data analysis
- Infrequent but large queries
- OLAP workloads

**When to use AutoML**:
- Need custom model
- Have labeled data
- Lack ML expertise
- Pre-trained APIs too generic

**When to use Pre-trained APIs**:
- Common use case (translation, vision, speech)
- Need fastest implementation
- No ML expertise
- No custom data required

**When to use Vertex AI Custom Training**:
- Need maximum control
- Have ML expertise
- Unique business problem
- Competitive differentiation required

---

# EXAM PRACTICE QUESTIONS (289 Total)

## GCP to AWS Service Quick Reference Map

| GCP Service                 | AWS Equivalent           | Key Use Case            | Exam Tip                                |
| --------------------------- | ------------------------ | ----------------------- | --------------------------------------- |
| **Compute Engine**          | EC2                      | VMs, IaaS               | Use for full control, lift-and-shift    |
| **Cloud Run**               | Fargate + App Runner     | Serverless containers   | Scales to zero, fastest deployment      |
| **Cloud Functions**         | Lambda                   | Event-driven serverless | Database triggers, lightweight code     |
| **GKE**                     | EKS                      | Kubernetes              | Complex microservices                   |
| **App Engine**              | Elastic Beanstalk        | PaaS web apps           | Balance of control & management         |
| **Cloud Storage**           | S3                       | Object storage          | Standard/Nearline/Coldline/Archive      |
| **Cloud SQL**               | RDS                      | Managed relational DB   | MySQL, PostgreSQL, SQL Server           |
| **Cloud Spanner**           | Aurora Global            | Global distributed SQL  | Global consistency, horizontal scale    |
| **Bigtable**                | DynamoDB                 | NoSQL, high throughput  | IoT, time-series, millions of sensors   |
| **Firestore**               | DynamoDB + DocumentDB    | Document database       | Mobile/web apps, real-time sync         |
| **BigQuery**                | Redshift + Athena        | Data warehouse          | OLAP, analytics, petabyte-scale         |
| **Dataflow**                | Kinesis Data Analytics   | Stream/batch processing | Auto-scaling pipelines                  |
| **Pub/Sub**                 | SNS + SQS                | Messaging               | Async communication, event-driven       |
| **Cloud VPN**               | Site-to-Site VPN         | Hybrid connectivity     | **Fast setup**, encrypted over internet |
| **Cloud Interconnect**      | Direct Connect           | Dedicated connection    | **Slow setup**, private, no internet    |
| **Partner Interconnect**    | Direct Connect (Partner) | Via network provider    | Sensitive data, no public internet      |
| **Cloud CDN**               | CloudFront               | Content delivery        | Low latency, global distribution        |
| **Cloud Armor**             | WAF + Shield             | DDoS protection         | Web app security                        |
| **Security Command Center** | Security Hub             | Compliance monitoring   | Org-wide security posture               |
| **IAM**                     | IAM                      | Access management       | Least privilege                         |
| **Cloud Build**             | CodeBuild                | CI/CD builds            | Automate build/test/deploy              |
| **Container Registry**      | ECR                      | Container images        | Store images for Cloud Run              |
| **Artifact Registry**       | ECR + CodeArtifact       | Artifacts + packages    | Replaces Container Registry             |
| **Cloud Logging**           | CloudWatch Logs          | Log management          | Audit trails                            |
| **Cloud Monitoring**        | CloudWatch               | Metrics & monitoring    | Performance tracking                    |
| **Dataprep**                | Glue DataBrew            | Visual data prep        | Interactive data cleaning               |
| **Data Fusion**             | Glue                     | ETL service             | Visual ETL pipelines                    |
| **Dataproc**                | EMR                      | Managed Hadoop/Spark    | Big data processing                     |
| **Firebase**                | Amplify + Mobile Hub     | Mobile backend          | Full mobile platform                    |
| **Identity-Aware Proxy**    | -                        | Context-aware access    | App-level access control                |
| **Private Google Access**   | VPC Endpoints            | Private API access      | VMs without external IPs                |


## Key Exam Patterns & Decision Trees

### Compute Selection

```
Need full OS control? → Compute Engine (EC2)
Containerized app, serverless? → Cloud Run (Fargate)
Event-driven, lightweight? → Cloud Functions (Lambda)
Complex microservices? → GKE (EKS)
Simple web app, PaaS? → App Engine (Beanstalk)
```

### Database Selection

```
Relational, regional? → Cloud SQL (RDS)
Relational, global? → Cloud Spanner (Aurora Global)
NoSQL, high throughput? → Bigtable (DynamoDB)
Document, mobile/web? → Firestore (DocumentDB)
Analytics, data warehouse? → BigQuery (Redshift)
```

### Storage Selection

```
Frequent access? → Standard Storage
Monthly access? → Nearline Storage
Quarterly access? → Coldline Storage
Yearly access? → Archive Storage
```

### Connectivity Selection

```
Need fast setup? → Cloud VPN (over internet)
Need dedicated, private? → Cloud Interconnect (slow setup)
Sensitive data, no internet? → Partner Interconnect
```

## High-Yield Practice Questions

### Q1: Global Data Residency

**Scenario:** Serve customers worldwide, data must stay in specific geographic area
**Answer:** Public cloud with guaranteed data location
**AWS Parallel:** Use AWS Regions with data residency controls
**Why:** Public cloud offers global reach + regional compliance

### Q2: Short-Term Compute (2 weeks)

**Scenario:** Need extra compute for 2 weeks only
**Answer:** On-demand VM (no committed use discount)
**AWS Parallel:** EC2 On-Demand (not Reserved Instances)
**Why:** Pay-as-you-go for temporary workloads

### Q3: Cloud Cost Planning

**Scenario:** How often to review cloud costs?
**Answer:** Frequently (costs change based on usage)
**AWS Parallel:** Use Cost Explorer regularly
**Why:** Cloud costs are dynamic, not fixed like on-prem

### Q4: Security Vulnerability Scanning

**Scenario:** Identify VMs with outdated OS images
**Answer:** Security Command Center
**AWS Parallel:** AWS Security Hub + Inspector
**Why:** Centralized security posture management

### Q5: Windows License Optimization

**Scenario:** Windows VMs only used during work hours, licenses expiring
**Answer:** Migrate to Compute Engine with PAYG licensing
**AWS Parallel:** EC2 with License Included pricing
**Why:** Pay per-second, eliminate weekend license costs

### Q6: Low Latency + Redundancy

**Scenario:** <10ms latency between VMs, need redundancy
**Answer:** Different zones within same region
**AWS Parallel:** Multi-AZ deployment in same region
**Why:** Zones are close (low latency) but separate (redundancy)

### Q7: Public Cloud Responsibilities

**Scenario:** What does cloud provider own?
**Answer:** Hardware maintenance + Hardware capacity management
**AWS Parallel:** Same shared responsibility model
**Why:** Provider manages physical infrastructure

### Q8: Rendering Workload (Interruptible)

**Scenario:** <12 hours per job, can be interrupted, no SLA
**Answer:** Preemptible instances
**AWS Parallel:** EC2 Spot Instances
**Why:** 80% cost savings for interruptible workloads

### Q9: Restrict External IPs Org-Wide

**Scenario:** Prevent all VMs from having external IPs, new projects coming
**Answer:** Organization policy at root node
**AWS Parallel:** Service Control Policies (SCPs)
**Why:** Inherited by all folders/projects automatically

### Q10: Stop Managing Infrastructure

**Scenario:** Manage workloads globally, stop infrastructure management
**Answer:** Migrate to public cloud
**AWS Parallel:** Same - use AWS managed services
**Why:** Cloud abstracts infrastructure management

### Q11: Sensitive Data, No Public Internet

**Scenario:** On-prem data can't traverse public internet
**Answer:** Partner Interconnect
**AWS Parallel:** Direct Connect
**Why:** Dedicated private connection, bypasses internet

### Q12: Cloud Run Image Storage

**Scenario:** Store container images for Cloud Run deployment
**Answer:** Container Registry (now Artifact Registry)
**AWS Parallel:** Amazon ECR
**Why:** Native integration with container services

### Q13: SaaS vs PaaS vs IaaS

**Scenario:** Minimize customer management
**Answer:** SaaS
**AWS Parallel:** Use SaaS products (Salesforce, Workday)
**Why:** Provider manages everything except data/users

### Q14: Slow VM Rolling Updates

**Scenario:** OS boot times slow down deployments
**Answer:** Convert to containers
**AWS Parallel:** Use Docker + ECS/EKS
**Why:** Containers start in seconds, not minutes

### Q15: Active Directory Integration

**Scenario:** Remove Google access when AD account terminated
**Answer:** Configure Single Sign-On (SSO)
**AWS Parallel:** AWS SSO with AD integration
**Why:** Centralized identity, automatic deprovisioning

### Q16: Multi-Country Acquisitions

**Scenario:** Reduce overhead, low cost, maintain security
**Answer:** Host all services on public cloud
**AWS Parallel:** Consolidate to AWS
**Why:** Economies of scale, managed services

### Q17: Standard vs Coldline Storage

**Scenario:** What's the difference?
**Answer:** Coldline is for infrequently accessed data
**AWS Parallel:** S3 Standard vs Glacier
**Why:** Lower storage cost, higher retrieval cost

### Q18: Near-Unlimited Compute

**Scenario:** Need unlimited resources without procurement
**Answer:** Public cloud
**AWS Parallel:** AWS elasticity
**Why:** On-demand scaling, no hardware procurement

### Q19: Event-Driven Follower Notifications

**Scenario:** Respond to database writes, scale to zero, integrate with Pub/Sub
**Answer:** Cloud Functions
**AWS Parallel:** Lambda with DynamoDB Streams
**Why:** Serverless, event-driven, auto-scales to zero

### Q20: IoT Sensor Data (Millions of Devices)

**Scenario:** Worldwide, high-speed, large unstructured data
**Answer:** Cloud Bigtable
**AWS Parallel:** DynamoDB or Timestream
**Why:** NoSQL, high throughput, global scale

### Q21: Streaming Data Pipelines

**Scenario:** Managed service, auto-scaling, no server management
**Answer:** Dataflow
**AWS Parallel:** Kinesis Data Analytics
**Why:** Fully managed, serverless stream processing

### Q22: Automate Build/Test/Deploy

**Scenario:** Reduce manual work in CI/CD
**Answer:** Cloud Build
**AWS Parallel:** CodeBuild + CodePipeline
**Why:** Managed CI/CD platform

### Q23: Org-Wide Compliance Monitoring

**Scenario:** Report compliance across all projects
**Answer:** Security Command Center
**AWS Parallel:** AWS Security Hub
**Why:** Centralized security and compliance view

### Q24: Fast Private Connectivity Setup

**Scenario:** Connect on-prem to cloud ASAP
**Answer:** Cloud VPN
**AWS Parallel:** Site-to-Site VPN
**Why:** Quick setup over internet (vs Interconnect)

### Q25: Mobile App Platform

**Scenario:** Fully featured cloud platform for mobile
**Answer:** Firebase
**AWS Parallel:** AWS Amplify
**Why:** Complete mobile backend (auth, DB, storage, analytics)

## Rapid-Fire Concept Review

### Pricing Models

- **PAYG (Pay-As-You-Go):** Per-second billing, no commitment
- **Committed Use:** 1-3 year commitment, 57% discount
- **Preemptible/Spot:** 80% discount, can be terminated
- **Sustained Use:** Automatic discount for running >25% of month

### Storage Classes (GCP → AWS)

- **Standard → S3 Standard:** Frequent access
- **Nearline → S3 Standard-IA:** Monthly access, 30-day minimum
- **Coldline → S3 Glacier Instant:** Quarterly access, 90-day minimum
- **Archive → S3 Glacier Deep Archive:** Yearly access, 365-day minimum

### Connectivity Options (Speed to Setup)

1. **Cloud VPN** (Hours) - Encrypted over internet
2. **Partner Interconnect** (Weeks) - Via service provider
3. **Dedicated Interconnect** (Months) - Direct physical connection

### Compute Decision Matrix

| Requirement            | GCP Service                  | AWS Service  |
| ---------------------- | ---------------------------- | ------------ |
| Full control           | Compute Engine               | EC2          |
| Containers, serverless | Cloud Run                    | Fargate      |
| Event-driven           | Cloud Functions              | Lambda       |
| Kubernetes             | GKE                          | EKS          |
| PaaS web app           | App Engine                   | Beanstalk    |
| Batch jobs             | Compute Engine + Preemptible | Batch + Spot |


### Database Decision Matrix

| Data Type  | Access Pattern  | GCP Service   | AWS Service   |
| ---------- | --------------- | ------------- | ------------- |
| Relational | Regional        | Cloud SQL     | RDS           |
| Relational | Global          | Cloud Spanner | Aurora Global |
| NoSQL      | High throughput | Bigtable      | DynamoDB      |
| Document   | Mobile/web      | Firestore     | DocumentDB    |
| Analytics  | OLAP            | BigQuery      | Redshift      |
| In-memory  | Caching         | Memorystore   | ElastiCache   |


### Security Services

- **IAM:** Identity and access management
- **Security Command Center:** Org-wide security posture
- **Cloud Armor:** DDoS protection, WAF
- **Identity-Aware Proxy:** Context-aware access control
- **VPC Service Controls:** Perimeter security
- **Cloud KMS:** Key management
- **Secret Manager:** Secrets storage

### Migration Strategies (6 R's)

1. **Rehost:** Lift-and-shift (VMs)
2. **Replatform:** Lift-tinker-shift (managed services)
3. **Refactor:** Re-architect (cloud-native)
4. **Reimagine:** Rebuild from scratch
5. **Retain:** Keep on-premises
6. **Retire:** Decommission

### Cost Optimization Tips

- Review costs **frequently** (not annually)
- Use committed use discounts for steady workloads
- Use preemptible instances for fault-tolerant workloads
- Right-size VMs based on actual usage
- Use appropriate storage classes
- Delete unused resources
- Use Cloud Billing reports and budgets

### Compliance & Governance

- **Organization policies:** Enforce constraints at org/folder/project level
- **Audit logs:** Admin Activity, Data Access, System Event
- **Compliance reports:** PCI DSS, HIPAA, SOC 2, ISO 27001
- **Data residency:** Choose specific regions for data storage

## Exam Day Reminders

### Common Traps

- **Committed use discount** for short-term needs → Use on-demand
- **Cloud VPN** for sensitive data → Use Interconnect/Partner Interconnect
- **Single zone** for redundancy → Use multiple zones
- **Annual cost review** → Review frequently
- **Manual compliance** → Use Security Command Center
- **Physical hardware** for temporary needs → Use cloud VMs

### Quick Decision Rules

1. **Serverless first:** Cloud Run > GKE > Compute Engine
2. **Managed first:** Cloud SQL > self-managed DB on VMs
3. **Fast setup:** Cloud VPN > Interconnect
4. **Cost optimization:** Match access pattern to storage class
5. **Security:** Least privilege, organization policies, SCC
6. **Global scale:** Spanner (SQL), Bigtable (NoSQL), BigQuery (analytics)

### Time-Saving Keywords

- "Quickly/ASAP" → Cloud VPN, on-demand, Cloud Run
- "Cost-optimized" → Preemptible, appropriate storage class, PAYG
- "Serverless" → Cloud Functions, Cloud Run, App Engine
- "Global" → Cloud Spanner, Cloud CDN, multi-region
- "Sensitive data" → Partner Interconnect, CMEK, VPC Service Controls
- "Compliance" → Security Command Center, audit logs
- "Event-driven" → Cloud Functions, Pub/Sub
- "Analytics" → BigQuery, Dataflow
- "Mobile" → Firebase
- "Container" → Cloud Run, GKE, Artifact Registry

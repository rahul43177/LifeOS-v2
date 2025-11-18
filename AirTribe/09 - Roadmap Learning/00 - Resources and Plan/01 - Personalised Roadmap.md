[Web Roadmap](https://www.airtribe.live/roadmap/QE4EAOELPRU5)

# Skill gap analysis
- **Data Structures & Algorithms (DSA):**  
    Needs stronger problem-solving skills in core DSA topics (e.g., [[../../02 - DSA AirTribe/03 - Recursion/Recursion|recursion]], trees, graphs, DP), which are heavily tested in Tier 1 interviews.
- **System Design Skills:**  
    Build the ability to design scalable, distributed systems and articulate trade-offs involving performance, availability, and cost.
- **Object-Oriented and Low-Level Design:**  
    Gain hands-on experience designing modular, testable, and extensible systems using OOP, SOLID principles, and design patterns.
- **Computer Science Fundamentals:**  
    Requires deeper understanding of core CS concepts like memory management, operating systems basics, networking (HTTP/HTTPS, TLS), and databases (indexing, query optimization, transactions).
- **Backend Fundamentals:**
	Needs deeper understanding of backend architecture including API design, authentication/authorization, asynchronous processing (queues, schedulers), caching, logging, and performance monitoring. Improve fluency in core Node.js patterns (event loop, middleware, error handling), and DevOps fundamentals (CI/CD, deployment, containerization).
- **Open Source or Portfolio Projects:**  
    Establish a strong GitHub presence with clean, well-documented personal projects demonstrating architectural thinking and end-to-end implementation.
- **Sharpen Behavioural and Communication Skills:**  
    Prepare impactful STAR-format stories to demonstrate ownership, leadership, and decision-making in real-world engineering scenarios.
##### Resume analysis
- Refocus the resume headline/summary toward backend engineering, distributed systems, and scalability rather than full-stack/generalist positioning.
- Condense “SPOC/solo developer” phrasing into impact-driven metrics; FAANG recruiters look for scale, performance, and system design outcomes over ownership wording.
- Elevate backend-specific achievements (data pipelines, micro-services, caching, distributed workflows) and reduce frontend/UI mentions to avoid diluting backend focus.
- Highlight scale and performance metrics consistently (e.g., throughput handled, latency reduced, concurrent users supported) to show impact at FAANG-level scale.
- Strengthen technical skills section: prioritise backend stacks
- Streamline structure to one crisp page: Summary → Key Skills → Experience → Projects → Education → Certifications (if any).
##### Projects to build
- **Simple Chat Application** → Built a real-time chat system using WebSockets with persistent message storage and basic user session management.
- **URL Shortener** → Designed a hash-based URL shortening service with redirect handling and lightweight analytics (click counts, timestamps).
- **To-Do List API** → Developed a REST API supporting CRUD operations, JWT-based authentication, and role-based access control.
- **Real-time Notification System** → Engineered a notification service with WebSocket push delivery, email queues, and retry mechanisms.
##### Interview prep strategy
### **1. Data Structures & Algorithms (DSA)**
#### **Strategy:**
- **Phased Complexity**:
    - **Phase 1**: Focus on core patterns (e.g., Sliding Window, Binary Search, Two Pointers, Recursion, DFS/BFS)
    - **Phase 2**: Tackle intermediate topics (Backtracking, Tries, Heaps, Union-Find, Prefix Sum)
    - **Phase 3**: Master FAANG-heavy topics
- **Daily Timed Practice**:
    - Simulate interview environment (90 mins per session, 2–3 problems per session).
    - Use **LeetCode Premium Company Tags** (FAANG filters) + **Leetcode 75** and **Top Ranked 100**
- **Pattern-Based Mastery:**
    - Maintain a “Pattern Log” → Map problems to core techniques (like Palindrome = 2D DP + Two Pointers)
    - Focus on reusable paradigms like Top-K, Merge Intervals, Subsets/Permutations
- **Contests & Edge-Case Handling:**
    - Weekly contests on **LeetCode**, **Codeforces**, or **AtCoder** to improve speed, edge-case thinking, and handling pressure.
- **Tracking & Analytics:**
    - Maintain a Notion / Excel tracker by:
        - Topic, difficulty, company tag, time taken, failed test cases, what went wrong
- **Toolkits**:
    - Leetcode (Top Interview 150, Premium company tags)
    - NeetCode / Blind 75 / Striver’s A2Z
    - Weekly contest participation for edge-case practice

### **2. Low-Level Design (LLD)**
#### **Strategy:**
- **Core Concepts First**:  
    Practice applying SOLID principles, OOP, and design patterns.
- **Structure Answers Like Interviews**:
    - Clarify requirements
    - Identify core classes/entities
    - Define relationships and responsibilities
    - Discuss trade-offs and improvements
- **Mock LLD Sessions**:  
    Practice whiteboard-style explanations weekly and receive feedback from peers or mentors.

### **3. High-Level System Design (HLD)**
#### **Strategy:**
- **Framework First**:  
    Always structure answers:
    - Requirements → API & DB design → Components → Bottlenecks → Scaling
- **Master Core Components**:
    - Load balancer, CDN, Cache, Queues, Databases (SQL/NoSQL), Sharding
- **Compare Designs**:  
    Practice evaluating multiple architectural trade-offs (e.g., CQRS vs Monolith)
- **Diagram Practice (Draw Every Design):**
    - Logical architecture, data flow, sequence diagrams, scaling plan
- **Design Tradeoff Thinking:**
    - Always present pros/cons (e.g., monolith vs microservice, SQL vs NoSQL)
### **4. Behavioral Interviews (HR/Managerial Rounds)**
#### **Strategy:**

- **STAR Format**:
    - Prepare 10+ stories across themes: Leadership, Conflict Resolution, Mistakes, Ownership, Teamwork
    - Focus on _“Impact + Metrics + Learnings”_
- **Practice Aloud**:
    - Record answers and get peer feedback
- **Common Questions**:
    - Tell me about a time you disagreed with a manager.
    - Describe a challenging technical decision you made.
    - How do you deal with ambiguity or incomplete requirements?

### **References**

- [DSA Common Patterns: ](https://docs.google.com/document/d/1DfiS3sAoDXq-OrFWB1pW3J7BIpfB_ROn66RgtALbigA/edit?usp=sharing)
- [STAR Method](https://docs.google.com/document/d/1Ecuusxjp78q8z50JGjzX2LMOpm-KwKO1OfqJd8G02D8/edit?usp=sharing)
- [DSA Tracker](https://docs.google.com/spreadsheets/d/1o2yMpcTmjya-hUyk3BqaflB-x9SFd02HWqk-9c6SeAE/edit?usp=sharing)
# Resources
### **Data Structures & Algorithms**

**Primary:**
- LeetCode (focus on patterns, not just problem count)
- Cracking the Coding Interview
- Algorithm Design Manual
**Secondary:**
- Data Structures and Algorithms with Javascript - Michael McMillan
- Elements of Programming Interviews
- InterviewBit
### **Low Level Design**
**Books:**
- "Design Patterns" by Gang of Four
- "Clean Architecture" by Robert Martin
- "Building Microservices" by Sam Newman
- “Learning JavaScript Design Patterns” by Addy Osmani

**Online:**
- Refactoring Guru (design patterns)
- Grokking the Low Level Design
### **Backend Fundamentals**

- [MDN Web Docs – HTTP Overview](https://developer.mozilla.org/en-US/docs/Web/HTTP)
- Auth0 Blog – Auth in Node.js
- [Express.js Official Docs](https://expressjs.com/)
- [MongoDB University – Node.js Driver Course](https://university.mongodb.com/)
- [Node.js + MySQL Guide](https://github.com/mysqljs/mysql)

### **GenAI**
- LangChain.js Docs – [https://js.langchain.com](https://js.langchain.com)
- Transformers.js – [https://xenova.github.io/transformers.js](https://xenova.github.io/transformers.js)
- OpenAI Node.js SDK – [https://github.com/openai/openai-node](https://github.com/openai/openai-node)
- Pinecone Node.js Client – [https://docs.pinecone.io/docs/node-client](https://docs.pinecone.io/docs/node-client)
- Prompt Engineering Guide ([DAIR.AI](http://DAIR.AI)) – [https://www.promptingguide.ai](https://www.promptingguide.ai)

# 6-month high level roadmap
## **Month 1: Foundations & Core Backend Skills**
**Goals**
- Refresh core backend/web concepts
- Build small but production-like projects
- Strengthen DSA fundamentals    
### **Backend Fundamentals**
- **HTTP & REST**: verbs, headers, cookies, CORS, status codes
- **Express.js basics**: middleware, routing, error handling
- **CRUD API Project**: user & todo management (JWT authentication, error handling, logging)
- **SQL Basics**: schema design, primary/foreign keys, joins, indexes
### **Data Structures & Algorithms**
- Arrays, Strings, LinkedLists, Stacks, Queues, Hash Maps
- Patterns: Two Pointers, Sliding Window, HashMap frequency, Stack-based problems
- **Target**: 40–50 problems (LeetCode Easy/Medium mix)
### **Low Level Design**
- SOLID principles, OOP basics, UML
- Practice: Parking Lot, Vending Machine, ATM
### **High Level Design (Intro)**
- Horizontal vs vertical scaling 
- SQL vs NoSQL
- Simple practice: URL Shortener
### **GenAI**
- Learn basics of LLMs, embeddings, and prompts.
- Get comfortable with OpenAI Node.js SDK & LangChain.js.
- Build first apps: CLI chatbot, prompt-based summarizer, and FAQ bot.
## **Month 2: Intermediate Backend + Interview Readiness**
**Goals**
- Start applying for interviews
- Learn intermediate backend concepts
- Expand DSA into Trees/Graphs/Heaps
### **Backend Fundamentals**
- **API Architecture**: versioning, pagination, rate limits
- **Async Programming**: Promises, async/await, callbacks
- **Error Handling & Logging**: Winston, Pino, centralized logs
- **Database Schema Design**: one-to-many, many-to-many, normalization vs denormalization
### **Data Structures & Algorithms**
- Trees & BSTs (DFS, BFS)
- Graphs (BFS, DFS, shortest path basics)
- Binary Search (patterns & variations)
- Heaps/Priority Queues
- **Target**: 50–60 problems
### **Low Level Design**
- Concurrency basics (thread-safe counter)
- API design principles
- Practice: Cache (LRU), Rate Limiter, Pub-Sub System
### **High Level Design**
- Message Queues, Event-driven basics
- Microservices intro
- Practice: Twitter timeline, Notification System
### **GenAI**
- Apply LangChain.js for chaining and memory.
- Build document Q&A system with Retrieval-Augmented Generation (RAG).
- Explore multimodal APIs (text + image).
- Add logging and error handling in Gen-AI apps.
## **Month 3: Advanced Patterns & Scaling**
**Goals**
- Handle advanced algorithms
- Learn distributed backend concepts
- Work on scalable design exercises
### **Backend Fundamentals**
- **Caching**: Redis (in-memory, TTL, eviction)
- **Performance Tuning**: profiling, database indexes, query optimisation
- **Messaging**: Kafka/RabbitMQ basics, pub-sub vs queues
### **Data Structures & Algorithms**
- Advanced DP (1D, 2D)
- Union-Find & Topological Sort
- Tries & String algorithms (KMP, Rabin-Karp basics)
- **Target**: 50–60 problems
### **Low Level Design**
- Distributed Cache
- Message Queue
- Database Engine (simplified)
### **High Level Design**
- CAP Theorem, Consistency Models
- Fault tolerance, replication
- Practice: WhatsApp, Instagram, Netflix
### **GenAI**
- Improve RAG with chunking and hybrid search.
- Experiment with lightweight agents (tool-using bots).
- Build chatbots connected to external APIs (weather, stock, Wikipedia).
- Deploy first portfolio-ready RAG chatbot with a simple frontend.
## **Month 4: System Design Mastery**
**Goals**
- Build confidence in LLD + HLD discussions
- Learn advanced distributed systems concepts
- Focus on trade-offs
### **Backend Fundamentals**
- **Microservices Best Practices**: service decomposition, API gateway, service discovery
- **Observability**: health checks, metrics, logs, traces (Prometheus, ELK basics)
### **Data Structures & Algorithms**
- Segment Trees / Fenwick Trees (basic understanding is enough)
- Advanced DP optimizations
- Math problems & company-specific patterns
- **Target**: 40–50 problems
### **Low Level Design**
- Deep dive into specific patterns and technologies. Some example systems:
    - Real-time Analytics System
    - Workflow Engine
    - Recommendation Engine
### **High Level Design**
- Event Sourcing, CQRS
- Security & compliance basics (OAuth2, RBAC)
- Practice: E-commerce (Amazon), Google Drive, Payment System
### **GenAI**
- Implement streaming responses & cost optimization.
- Add guardrails (prompt injection prevention, PII protection).
- Introduce observability: log prompts, responses, and latency.
- Build second portfolio-ready domain chatbot (e.g., Healthcare, E-commerce, or EdTech).
## **Month 5: Domain Expertise + Portfolio Projects**
**Goals**
- Apply knowledge to real-world problems
- Create strong portfolio projects
- Prepare for company-specific patterns
### **Backend Fundamentals**
- **DevOps Basics**: Dockerise backend project, CI/CD with GitHub Actions/Jenkins
- **Domain Backends**:
    - E-commerce (cart, payments, inventory)
    - Streaming (video buffering, CDNs)
### **Data Structures & Algorithms**
- Company-specific practice (FAANG, startups) under timed conditions
- Emphasis on explaining thought process
### **Low Level Design**
- Study actual system architectures. Examples:
    - YouTube video processing
    - Slack messaging system
    - GitHub version control
- Understand production challenges
- Learn from engineering blogs
### **High Level Design**
- Inter-service communication (REST/gRPC, async messaging)
- Messaging queues (Kafka, RabbitMQ, SQS)
- Asynchronous processing, pub-sub vs message queues
### **GenAI**
- Specialize in applied use cases (E-commerce assistant, EdTech tutor, Knowledge management bot).
- Focus on building one polished domain project that can go on GitHub + resume.
- Ensure deployments are production-ready (Vercel/AWS + CI/CD).
### **Portfolio Projects (choose 1–2)**
- Scalable chat app (with Redis/Kafka + Node backend)
- E-commerce backend (payment flow + inventory management)
- LLM-powered backend microservice (bonus if interested in GenAI roles)
## **Month 6: Interview Excellence & Final Prep**
**Goals**
- Become interview-ready across DSA, LLD, HLD
- Mock interviews & timed practice
- Refine portfolio
### **Backend Fundamentals**
- Final revisions: latency, throughput, fault tolerance
- Build: production-ready REST API with observability & fault tolerance
### **Data Structures & Algorithms**
- Daily timed contests (LeetCode, Codeforces)
- Focus on communication, edge cases, debugging
### **Low Level Design**
- Ambiguous requirements practice
- Redesign existing systems for performance or cost optimization
### **High Level Design**
- Streaming vs Batching (high-level overview only)
- Practice Capstone:
    - Google Search
    - Facebook
    - Multi-tenant SaaS platform
### **GenAI**
- Practice Gen-AI system design: RAG architecture, vector DB trade-offs, cost vs accuracy.
- Do mock interviews (backend + Gen-AI hybrid).
- Debug common issues (hallucinations, bad queries, empty responses).
- Final polish: portfolio, demo videos, and GitHub projects.
### **Final Prep**
- 3 DSA mocks/week
- 2 LLD mocks/week
- 2 HLD mocks/week
- Behavioural interview practice (STAR method)



[[Simplified - broken down Roadmap to follow]]
[[Month-Wise Breakdown/Month - 01 - November]]
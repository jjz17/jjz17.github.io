---
layout: default
title: Jason Zhang | Data Science and Software Development Portfolio
---

<!-- Toggle Button -->
<button id="toc-toggle" class="toc-toggle-btn">☰</button>

<!-- TOC Container -->
<div class="toc-container hidden" id="toc">
    <ul>
        <li><a href="#about">About Me</a></li>
        <li><a href="#work-experience">Work Experience</a></li>
        <li><a href="#education">Education</a></li>
        <li><a href="#technical-skills">Technical Skills</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#open-source">Open Source</a></li>
        <!-- <li><a href="#blog">Blog</a></li> -->
    </ul>
</div>

## <a id="about"></a>👨‍💻 About Me

<!-- ![Profile Picture](assets/images/profile.jpeg) -->
Hi, I'm Jason, an ambitious **Data Scientist and Software Developer** passionate about leveraging technology to solve complex business problems. 

I have operationalized **LLM RAG** applications, built **scalable data pipelines**, and **deployed ML/software solutions** across my experiences at U.S. DOT, Wolters Kluwer, and MORSE Corp. My expertise spans **data science, data engineering, machine learning, and software development**. 

I am eager to contribute to **high-impact, data-driven solutions** and continuously expand my expertise in AI, infrastructure, and software scalability.  

---

## <a id="work-experience"></a>💼 Featured Work Experience

<div class="card-container">
 <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/usdot.png" alt="Company Logo" class="company-logo">
      <h3>Data Scientist</h3>
      <p>U.S. DOT Volpe Center</p>
      <p class="location">Cambridge, MA</p>
      <p class="time">Jul 2024 - Present</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Engineered <strong>ETL pipelines</strong> using Apache Airflow and AWS Glue for processing <strong>20,000+ records annually</strong>, reducing data processing time by <strong>60%</strong>.</li>
        <li>Prototyped <strong>LLM Retrieval-Augmented Generation (RAG) models</strong> with Hugging Face Transformers, enhancing documentation retrieval efficiency by <strong>30%</strong>, saving <strong>200+ hours annually</strong>.</li>
        <li>Authored comprehensive memos on <strong>NIST AI RMF</strong>, promoting <strong>AI risk management adoption</strong> across teams.</li>
    </ul>
    </div>
  </div>
  
  <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/wolters.png" alt="Company Logo" class="company-logo">
      <h3>SWE Co-op</h3>
      <p>Wolters Kluwer</p>
      <p class="location">Boston, MA</p>
      <p class="time">Jul 2023 - Jan 2024</p>
    </div>
    <div class="card-back">
        <ul>
            <li>Developed a <strong>Spring Boot microservice</strong> leveraging Google Cloud Translation API to process <strong>100,000+ medical documents daily</strong>.</li>
            <li>Re-implemented backend image retrieval using <strong>Elasticsearch, S3, and JAX-RS</strong>, reducing load times by <strong>20%</strong>.</li>
            <li>Enhanced <strong>user data schema</strong> for improved password security and deployed updates to production.</li>
            <li>Streamlined infrastructure by retiring a legacy microservice with <strong>Docker</strong> and <strong>Jenkins</strong>, decreasing global server load.</li>
        </ul>
    </div>
  </div>

   <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/nu.png" alt="Company Logo" class="company-logo">
      <h3>Data Engineer</h3>
      <p>NEU Khoury College</p>
      <p class="location">Boston, MA</p>
      <p class="time">Dec 2022 - May 2023</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Re-architected databases with <strong>Redis distributed clusters</strong>, improving computation framework speed by <strong>20%</strong>.</li>
        <li>Leveraged <strong>Redis Cloud</strong> for 99.99% uptime, ensuring scalability and durability.</li>
        <li>Refactored codebase with <strong>OOP principles</strong> and implemented automated testing for maintainability.</li>
    </ul>
    </div>
  </div>
  
  <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/morse.png" alt="Company Logo" class="company-logo">
      <h3>Data Science Co-op</h3>
      <p>MORSE Corp</p>
      <p class="location">Cambridge, MA</p>
      <p class="time">Jul 2022 - Jan 2023</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Implemented a <strong>time series bootstrap method</strong> in NumPy to estimate statistical uncertainty in temporal data.</li>
        <li>Optimized dataset splits, reducing preprocessing time by <strong>30%</strong>, and created a reusable <strong>EDA and synthetic data library</strong> used by 8 engineers.</li>
        <li>Maintained <strong>ETL pipelines</strong> with PySpark, reducing data lag by <strong>15%</strong> and automating documentation via Dockerized CI/CD pipelines.</li>
    </ul>
    </div>
  </div>
</div>

&nbsp;

---

## <a id="education"></a>📚 Education

<div class="card-container">
 <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/nu.png" alt="Company Logo" class="company-logo">
      <h3>M.S. Bioinformatics</h3>
      <p>NEU College of Science</p>
      <p class="location">Boston, MA</p>
      <p class="time">Sep 2024 - May 2026</p>
    </div>
    <div class="card-back">
    <ul>
        <li><strong>GPA:</strong> 4.0</li>
        <li><strong>Coursework:</strong></li>
        <!-- <li><strong>Coursework:</strong> Bioinformatics Programming, Computational Methods in Bioinformatics, Algorithms, Statistics for Bioinformatics.</li> -->
        <li>Bioinformatics Programming</li>
        <li>Computational Methods in Bioinformatics</li>
        <li>Algorithms</li>
        <li>Statistics for Bioinformatics</li>
    </ul>
    </div>
  </div>
  
  <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/nu.png" alt="Company Logo" class="company-logo">
      <h3>B.S. Data Science and Mathematics</h3>
      <p>NEU Khoury College</p>
      <p class="location">Boston, MA</p>
      <p class="time">Sep 2020 - May 2024</p>
    </div>
    <div class="card-back">
    <ul>
        <li><strong>GPA:</strong> 4.0</li>
        <li><strong>Coursework:</strong></li>
        <li>Machine Learning</li>
        <li>Large-Scale Data Storage</li>
        <li>Data Science Foundations</li>
        <li>Object-Oriented Design</li>
        <li>Stochastic Probability</li>
        <li>Linear Algebra</li>
    </ul>
    </div>
  </div>
</div>

&nbsp;

---

## <a id="technical-skills"></a>👩‍💻 Technical Skills

- **Languages**: Python, SQL, Java, R, Bash, TypeScript, Scala
- **Data Science**: Pandas, NumPy, PyTorch, TensorFlow, NLTK, spaCy, Scikit-learn, XGBoost
- **Data Engineering**: Apache Airflow, Docker, Spark, Kubernetes, MongoDB, Redis, Neo4j  
- **Tools & Frameworks**: AWS, GCP, Tableau, ELK Stack, Jenkins, JAX-RS, Spring Boot, Tomcat

---

## <a id="projects"></a>🚀 Projects

<div class="card-container">
 <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/scheduler.png" alt="Company Logo" class="company-logo">
      <h3><a href="https://github.com/jjz17/TaskScheduler" target="_blank">TaskScheduler</a></h3>
      <p>Task Optimization Framework</p>
      <p class="location">Skills: Python, Flask, SQL, Redis</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Developed a <strong>custom task scheduling application</strong> to automate and manage recurring tasks.</li>
        <li>Implemented <strong>cron-like scheduling</strong> with support for complex recurrence patterns.</li>
        <li>Designed a <strong>user-friendly interface</strong> for easy task creation and monitoring.</li>
        <li>Ensured <strong>robust error handling</strong> and logging mechanisms for reliable task execution.</li>
    </ul>
    </div>
  </div>

   <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/airflow.png" alt="Company Logo" class="company-logo">
      <h3><a href="https://github.com/jjz17/AirflowIQ" target="_blank">AirflowIQ</a></h3>
      <p>Scalable Workflow Automation</p>
      <p class="location">Skills: Airflow, Docker, SQL</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Created a <strong>monitoring tool for Apache Airflow</strong> to track DAG performance and failures.</li>
        <li>Integrated with the <strong>ELK Stack (Elasticsearch, Logstash, Kibana)</strong> for real-time log analysis.</li>
        <li>Developed an <strong>automated alerting system</strong> to notify users of pipeline issues.</li>
        <li>Deployed on <strong>AWS EC2 and S3</strong> for scalable and resilient workflow tracking.</li>
    </ul>
    </div>
  </div>

 <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/vector-db.png" alt="Company Logo" class="company-logo">
      <h3><a href="https://github.com/jjz17/VectorDB" target="_blank">VectorDB</a></h3>
      <p>Vector Database Implementation</p>
      <p class="location">Skills: NumPy, Jupyter, Vector Search</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Implemented a <strong>vector database</strong> as a study project to understand database internals.</li>
        <li>Focused on <strong>efficient storage and retrieval</strong> of high-dimensional vectors.</li>
        <li>Utilized <strong>Python</strong> and <strong>Jupyter Notebooks</strong> for development and testing.</li>
        <li>Applied <strong>unit testing</strong> to ensure code reliability and correctness.</li>
    </ul>
    </div>
  </div>
  
  <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/cnn.png" alt="Company Logo" class="company-logo">
      <h3><a href="https://github.com/jjz17/Datathon2023" target="_blank">Photo Quality Prediction</a></h3>
      <p>Competition Top Performing XGBoost and CNN models</p>
      <p class="location">Skills: XGBoost, TensorFlow, OpenCV</p>
    </div>
    <div class="card-back">
        <ul>
            <li>Secured <strong>Second Place</strong> in the "Can I Be an Influencer?" Kaggle competition.</li>
            <li>Conducted <strong>exploratory data analysis (EDA)</strong> to uncover key insights.</li>
            <li>Developed a <strong>neural network model</strong> to predict influencer potential.</li>
            <li>Collaborated with team members using <strong>Jupyter Notebooks</strong> and <strong>Git</strong> for version control.</li>
        </ul>
    </div>
  </div>

   <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/dash.png" alt="Company Logo" class="company-logo">
      <h3><a href="https://github.com/jjz17/twitter-dashboard" target="_blank">Twitter Sentiment Dashboard</a></h3>
      <p>Flask dashboard for real-time analytics</p>
      <p class="location">Skills: NLP, Twitter API, Streamlit, Poetry</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Built a <strong>dashboard</strong> providing insights and analytics for personal Twitter accounts.</li>
        <li>Implemented <strong>data fetching</strong> from the Twitter API to gather user metrics.</li>
        <li>Designed <strong>interactive visualizations</strong> using <strong>JavaScript</strong> and <strong>D3.js</strong>.</li>
        <li>Packaged the application with <strong>Poetry</strong> for dependency management and streamlined deployment.</li>
    </ul>
    </div>
  </div>
  
  <!-- <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/tennis.png" alt="Company Logo" class="company-logo">
      <h3>Tennis Match Prediction</h3>
      <p>XGBoost model to predict outcomes of tennis matches</p>
      <p class="location">Skills: Python, Flask, Plotly, NLP</p>
    </div>
    <div class="card-back">
    <ul>
        <li>Implemented a <strong>time series bootstrap method</strong> in NumPy to estimate statistical uncertainty in temporal data.</li>
        <li>Optimized dataset splits, reducing preprocessing time by <strong>30%</strong>, and created a reusable <strong>EDA and synthetic data library</strong> used by 8 engineers.</li>
        <li>Maintained <strong>ETL pipelines</strong> with PySpark, reducing data lag by <strong>15%</strong> and automating documentation via Dockerized CI/CD pipelines.</li>
    </ul>
    </div>
  </div> -->
</div>

&nbsp;

---

## <a id="open-source"></a>🔓 Open Source

<div class="card-container">
 <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/coming.png" alt="Company Logo" class="company-logo">
      <h3>In Progress</h3>
      <p>...</p>
      <!-- <p class="location">Boston, MA</p>
      <p class="time">Sep 2024 - May 2026</p> -->
    </div>
    <div class="card-back">
    <ul>
        <li>...</li>
    </ul>
    </div>
  </div>
  
  <div class="card" onclick="toggleCard(this)">
    <div class="card-front">
      <img src="assets/images/coming.png" alt="Company Logo" class="company-logo">
      <h3>In Progress</h3>
      <p>...</p>
      <!-- <p class="location">Boston, MA</p>
      <p class="time">Sep 2020 - May 2024</p> -->
    </div>
    <div class="card-back">
    <ul>
        <li>...</li>
    </ul>
    </div>
  </div>
</div>

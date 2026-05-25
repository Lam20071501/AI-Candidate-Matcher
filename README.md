# AI-Candidate-Matcher
halo
## 1. Project Title & Problem Statement
Part 1: Corrected Problem Statement Text
Problem Statement: The Intelligent Recruiter

Challenge: Traditional job boards are static and inefficient. Your goal is to build an intelligent agent that bridges the gap between diverse talent and hiring managers.

The Mission: Create an agent that takes a job description and a pool of candidate data (resumes/profiles) and identifies the best matches.

## 2. Problem
Synonym blindness
"Engineered distributed systems" and "built microservices with Kafka" mean the same thing. ATS sees zero overlap. One passes, one fails --- based purely on word choice, not ability.

Years ≠ ability
"Requires 5 years experience" eliminates the person who did more in 3 years than another did in 8. Rule-based systems count time. They cannot measure growth velocity, impact, or output quality.

Invisible signals
Open source contributions, specific impact metrics ("reduced latency by 40%"), unconventional career paths, self-taught depth — all invisible to pattern matchers. These are often the strongest signals.

No gap reasoning
Missing "Kubernetes" in the requirement? Rejected — even if the candidate has Docker, ECS, and Helm. There is no concept of adjacent knowledge, learning curve, or how hard a gap actually is to close.


## 3. Solution
Semantic understanding
Reads "built a fault-tolerant message queue from scratch" and connects it to the requirement "experience with event-driven architecture" — not because a synonym table says so, but because it understands what both phrases mean in practice.

Trajectory inference
Can read a career timeline and reason: "Junior → mid in 14 months → led a team of 4 in year 3 → architecting independently by year 4. This person accelerates. The 4 years they have is functionally worth more than another candidate's 7 flat years."

Gap vs dealbreaker distinction
Not all missing skills are equal. The LLM distinguishes "has never used Terraform but has strong AWS CLI and Pulumi" (closable gap, 2 weeks) from "no backend experience at all for a senior backend role" (structural mismatch). It explains this reasoning explicitly.

Explainable, overridable decisions
Every ranking comes with a written rationale. The hiring manager reads exactly why candidate A scored 91 and candidate B scored 67. They can disagree, add context the agent didn't have, and override — with full visibility into the logic. No black box.

## 4. Systems Requirements & dependencies
1. Software Requirements
Python 3.x: Ensure you have Python installed (check by typing python --version in your terminal).

VS Code (or any IDE): Since you are using Visual Studio Code, ensure the Python Extension is installed.

Microsoft PowerPoint: Required only to view the final file once it is generated.

2. Required Python Dependencies
The script relies on the python-pptx library to handle the creation of slides. You must install these via your terminal or command prompt:
Bash

# This ensures compatibility with some legacy object handling used in the script
pip install collections-extended

## 5. Installation & Configuration Instructions
Provide clear, step-by-step instructions so the judges can run your application locally:

- Step 1: Sign up or log into an n8n environment (n8n Cloud, Self-Hosted, or Desktop).
- Step 2: Create a blank new workflow.
- Step 3: Import the provided workflow file (Click “Menu -> Import from File” inside the n8n editor and select the `candidate-matcher.json` file provided in this repository).
- Step 4: Set up credentials: Open the `OpenAI Chat Model` node and create new credentials, inserting your own active OpenAI API Key.

## 6. How to Run the Application

Follow these steps to test the candidate matching system:

1. Click on the `Prepare Input` node in the n8n canvas.
2. Edit the JSON input in this node to set up your mock candidate profiles and job description text.
3. Click the orange `Execute Workflow` button at the bottom of the screen.
4. Once the execution completes successfully, view the output in the final `Top 5 Candidates` node.

## 7. Explanation Workflow
Phase 1 · Intake & Data Preparation
What is it?
This phase is the starting point of the recruitment workflow. The system receives the Job Description (JD) and candidate CVs, then prepares all data for AI processing.
What happens?
•	Recruiter uploads the JD and candidate CVs 
•	ATS / Google Form / Webhook sends data into n8n 
•	Workflow automatically starts 
•	AI reads and analyses the JD 
•	AI extracts: 
o	Required skills 
o	Optional skills 
o	Seniority level 
o	Hidden expectations 
•	AI enriches candidate CVs into structured data 
Why important?
Traditional ATS only scans keywords.
This workflow understands meaning and context, making screening more accurate and fair.
Example
JD says:
•	“Kafka preferred” 
•	“Microservices” 
•	“Fast-paced startup” 
AI understands:
•	Event-driven systems experience matters 
•	Candidate should adapt quickly 
•	Independent working style needed 
Candidate CV says:
•	“Built fault-tolerant systems” 
AI converts into:
•	Distributed systems 
•	Backend engineering 
•	Event-driven architecture 
Easy Analogy
Like organising messy documents into clean labelled folders before evaluation starts.
______________
Phase 2 · Semantic Matching & Gap Analysis
What is it?
This phase compares candidate experience with job requirements based on meaning instead of exact keywords.
What happens?
•	AI matches similar technologies and experiences 
•	Detects equivalent skills 
•	Uses confidence scoring 
•	Analyses missing skills carefully 
•	Classifies gaps into: 
o	Closable gaps 
o	Serious mismatches 
o	Irrelevant gaps 
Why important?
Traditional ATS may reject strong candidates because wording differs.
This workflow understands related experiences and avoids unfair rejection.
Example
JD:
•	“Event-driven architecture” 
CV:
•	“Built message queues” 
Traditional ATS:
•	No keyword match 
LLM:
•	Strong semantic match 
Gap Example:
•	Candidate knows Pulumi but not Terraform 
•	AI identifies this as a learnable gap instead of rejection 
Easy Analogy
Like understanding two people mean the same thing even when using different words.
______________
Phase 3 · Candidate Growth & Hidden Signal Evaluation
What is it?
This phase evaluates candidate potential, growth speed, achievements, and hidden strengths.
What happens?
•	Measures career progression speed 
•	Detects leadership growth 
•	Evaluates responsibility expansion 
•	Finds hidden signals such as: 
o	GitHub projects 
o	Open-source contributions 
o	Technical blogs 
o	Public talks 
o	Side projects 
o	Quantified achievements 
Why important?
Some high-potential candidates may not have many years of experience but show strong growth and impact.
Example
Candidate:
•	Only 4 years experience 
•	Became Senior quickly 
•	Leading a team early 
AI may evaluate:
•	4 years experience ≈ 6–7 years effective capability 
Another example:
•	Maintains 2.4k star GitHub repository 
•	Reduced company costs by $180k/year 
These become valuable hidden strengths.
Easy Analogy
Not judging someone by how long they worked, but by how fast they improved and what they achieved.
______________
Phase 4 · Multi-Dimension Scoring & Explainability
What is it?
This phase calculates candidate scores and explains the reasoning behind every ranking.
What happens?
AI evaluates candidates using multiple dimensions:
•	Skill match 
•	Career trajectory 
•	Impact achieved 
•	Gap severity 
•	Hidden signals 
•	Culture fit 
The system then generates:
•	Overall score 
•	Sub-scores 
•	Strengths 
•	Weaknesses 
•	Risks 
•	Final recommendation 
Why important?
Prevents black-box AI decisions and makes the recruitment process more transparent.
Example
Candidate Score:
•	Skill Match: High 
•	Leadership: Strong 
•	Gap Severity: Low 
Final Score:
•	91/100 
AI Explanation:
•	Strong distributed systems experience 
•	Excellent impact metrics 
•	Small Terraform gap 
•	Limited senior-level tenure 
Easy Analogy
Like a teacher not only giving marks, but also explaining why the student received them.
______________
Phase 5 · Human Review & Continuous Learning
What is it?
This is the final decision-making phase where hiring managers review AI recommendations and provide feedback.
What happens?
Hiring manager can:
•	Approve candidate 
•	Reject candidate 
•	Override AI scores 
•	Add comments 
•	Give additional context 
The system stores:
•	Human corrections 
•	Override reasons 
•	Hiring patterns 
•	Feedback history 
Future workflows improve using this feedback.
Why important?
The final hiring decision always remains with humans, not AI.
Example
AI Score:
•	79 
Manager Override:
•	88 
Reason:
•	Hiring manager personally knows candidate’s strong expertise 
Easy Analogy
AI acts like a smart assistant that helps decision-making, while humans remain the final authority.

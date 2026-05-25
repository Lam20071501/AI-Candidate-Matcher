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

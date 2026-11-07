# aparna-mira-capstone-project
AI-powered multi-agent project intelligence assistant built with Langflow and Langfuse for grounded planning, risk assessment, status reporting, and milestone tracking.

**Mira: AI-Powered Project Intelligence Assistant**

Mira is a multi-agent AI project intelligence assistant built with Langflow and Langfuse. It helps PMs and TPMs generate grounded project plans, assess risks, report project status, and track milestones using supplied project data.

**Key Capabilities**

Mira consists of four specialist agents:

Planner Agent - Generates project phases, activities, deliverables, milestones, and timelines.
Risk Assessor Agent - Identifies project risks, impacts, and mitigation strategies.
Status Reporter Agent - Reports completed, in-progress, blocked, and to-do tasks.
Milestone Tracker Agent - Identifies upcoming and at-risk milestones and recommends actions.
Architecture

Mira uses a Router/Dispatcher multi-agent architecture.

User Request
 → Smart Router
 → Specialist Agent
 → Grounded Response

Routing
Route	Specialist
PLAN	Mira Planner
RISK	Mira Risk Assessor
STATUS	Mira Status Reporter
MILESTONE	Mira Milestone Tracker
Grounding Strategy

Mira treats the supplied project files as authoritative sources.

The agents are designed to:

Use only supplied project data.
Avoid inventing project facts, risks, milestones, dates, or task statuses.
Identify insufficient information rather than fabricate answers.
Verify user claims against available project data.
Distinguish unsupported proposals from established project facts.
Project Data

Mira uses:

project_description.txt
project_timeline.csv
project_risks.csv
sample_task_board.csv
eval_mira_inputs.txt
Langflow Flows

The solution contains five Langflow flows:

MIRA_MAIN_ROUTER
MIRA_PLANNER
MIRA_RISK
MIRA_STATUS
MIRA_MILESTONE

The Smart Router classifies the user's request and routes it to the appropriate specialist flow.

Observability

Langfuse is used for observability and evaluation of Mira's LLM workflows, including:

Execution tracing
Debugging
Grounding evaluation
Hallucination analysis
Latency
Model/token usage and cost where available
Evaluation

Mira is evaluated using the provided T1-T12 baseline test set.

Evaluation focuses on:

Routing accuracy
Groundedness
Task correctness
Hallucination control
Risk accuracy
Task/status accuracy
Milestone accuracy
Insufficient-information handling

Additional adversarial tests are used to verify that Mira does not accept unsupported user claims as project facts.

Example Queries
Planning

Generate a detailed project plan for the ABCDE Ltd. AI Adoption Project.

Risk Assessment

What are the top 3 risks for the ABCDE Ltd. project?

Status Reporting

Generate a Sprint 3 project status report.

Milestone Tracking

Which milestones are currently at risk?

Repository Structure

mira-project/

README.md
flows/
data/
evaluation/
screenshots/
docs/
Technologies
Langflow
Langfuse
Large Language Models
Multi-Agent Orchestration
Prompt Engineering
Grounded AI / Hallucination Control
Project Status
Planner Agent
Risk Assessor Agent
Status Reporter Agent
Milestone Tracker Agent
Smart Router
Multi-agent integration
Langfuse evaluation
T1-T12 final evaluation
Final documentation
Key Learning

During testing, unsupported user inputs were found to cause hallucinations in some agent responses. Grounding prompts were strengthened so that project files are treated as authoritative sources and unsupported user claims are not treated as project facts.

The updated agents were retested using both baseline and adversarial prompts.

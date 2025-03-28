LinkedIn Recruitment Multi-Agent System
Overview
This project implements an automated recruitment pipeline using a multi-agent system to:

Search for candidates on LinkedIn

Match candidates to job requirements

Generate outreach strategies

Produce comprehensive recruitment reports

The system leverages LangGraph for agent orchestration, Selenium for LinkedIn automation, and Ollama LLMs for decision making.

Key Features
Four specialized agents (Researcher, Matcher, Communicator, Reporter)

Automated LinkedIn scraping with Selenium

Web search integration via Serper API

Customizable job requirements through YAML configs

End-to-end workflow from candidate discovery to final report

System Architecture

graph TD
    A[Researcher] -->|Uses| B[LinkedIn Search]
    A -->|Uses| C[Serper Search]
    A --> D[Matcher]
    D -->|Uses| E[Scoring Tools]
    D --> F[Communicator]
    F -->|Uses| G[Outreach Tools]
    F --> H[Reporter]
    H --> I[Final Report]
Installation
Clone the repository:

bash
Copy
git clone https://github.com/yourusername/recruitment-agent.git
cd recruitment-agent
Install dependencies:

bash
Copy
pip install -r requirements.txt
Set up environment variables:

bash
Copy
export LINKEDIN_COOKIE="your_li_at_cookie"
export SERPER_API_KEY="your_serper_api_key"
Configuration
Edit the YAML files in config/ directory:

agents.yaml: Configure agent roles, goals and backstories

tasks.yaml: Define task descriptions and parameters

Usage
Run the main pipeline:

python
Copy
python main.py
Or integrate specific components:

python
Copy
from recruitment_agent import LinkedinClient, run

# Single search
client = LinkedinClient()
results = client.find_people("Python, JavaScript")

# Full pipeline
report = run(job_requirements)
Components
Core Agents
Researcher: Finds candidates on LinkedIn and the web

Matcher: Scores and filters candidates

Communicator: Generates outreach strategies

Reporter: Compiles final recommendations

Supporting Tools
linkedin_search_tool: Scrapes LinkedIn profiles

serper_search_tool: Web search via Serper API

scrape_website_tool: Extracts content from candidate websites

Customization
To adapt for different use cases:

Modify agent prompts in agents.yaml

Add new tools to the ToolNodes

Adjust the workflow graph in create_recruitment_graph()

Ethical Considerations
Comply with LinkedIn's Terms of Service

Implement rate limiting to avoid IP bans

Respect candidate privacy and data protection laws

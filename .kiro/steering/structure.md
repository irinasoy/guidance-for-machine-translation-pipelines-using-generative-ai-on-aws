# Project Structure

## Directory Layout

```
translation-workshop/
├── lab1-basic-translation.ipynb       # Lab 1: Problem identification (15 min)
├── lab2-self-evaluation.ipynb         # Lab 2: Iteration patterns (20 min)
├── lab3-knowledge-base.ipynb          # Lab 3: KB integration (20 min)
├── lab4-agentcore-deployment.ipynb    # Lab 4: Production deployment (25 min)
├── lab_helpers/                       # Shared Python modules
│   ├── production_agent.py            # AgentCore entrypoint
│   ├── translation_tools.py           # Custom @tool decorators
│   └── utils.py                       # Helper functions
├── infrastructure/                    # Infrastructure as Code
│   └── knowledge-base.yaml            # CloudFormation template
├── sample_data/                       # Sample data for labs
│   ├── aws_lambda_intro.txt           # AWS documentation sample
│   └── aws_terminology.csv            # EN-RU terminology pairs
├── requirements.txt                   # Python dependencies
├── README.md                          # Workshop guide
└── WORKSHOP_SUMMARY.md                # Build summary
```

## Lab Notebooks

Each notebook is a self-contained learning module with progressive complexity:

**Lab 1: Basic Translation** (`lab1-basic-translation.ipynb`)
- Creates basic Strands agent with Bedrock
- Performs one-shot translation
- Identifies quality issues
- Motivates need for iteration
- Duration: 15 minutes

**Lab 2: Self-Evaluation** (`lab2-self-evaluation.ipynb`)
- Implements evaluation tools
- Builds reflect-refine loop
- Demonstrates autonomous improvement
- Shows iteration count and reasoning
- Duration: 20 minutes

**Lab 3: Knowledge Base** (`lab3-knowledge-base.ipynb`)
- Deploys CloudFormation stack
- Creates Bedrock Knowledge Base
- Implements terminology validation
- Achieves production-quality output
- Duration: 20 minutes (+ 5-10 min deployment)

**Lab 4: AgentCore Deployment** (`lab4-agentcore-deployment.ipynb`)
- Packages agent for production
- Deploys to AgentCore Runtime
- Tests production endpoints
- Monitors with observability traces
- Duration: 25 minutes (+ 5-10 min deployment)

## Helper Modules (`lab_helpers/`)

**production_agent.py**
- AgentCore entrypoint for production deployment
- Defines all tools used in production
- Implements system prompt and workflow
- Entry point: `invoke(payload, context)` function

**translation_tools.py**
- Custom `@tool` decorators for agent
- Tool functions: `evaluate_translation_quality`, `query_terminology_kb`, `translate_text`, `refine_translation_section`
- Helper functions: `extract_technical_terms`, `format_translation_result`
- Used across all labs

**utils.py**
- AWS utility functions
- Formatting helpers: `print_section_header`, `print_success`, `print_info`
- AWS client initialization
- Region and account detection

## Infrastructure (`infrastructure/`)

**knowledge-base.yaml**
- CloudFormation template for Knowledge Base deployment
- Creates: KB, OpenSearch Serverless collection, IAM roles, data source
- Data source: `sample_data/aws_terminology.csv`
- Ingestion: Automatic after stack creation (5-10 min)

## Sample Data (`sample_data/`)

**aws_lambda_intro.txt**
- Real AWS Lambda documentation excerpt
- Used as translation source in labs
- Demonstrates technical content translation

**aws_terminology.csv**
- 20 AWS terminology pairs (English-Russian)
- Format: `term_en,term_ru`
- Ingested into Knowledge Base for validation
- Examples: Lambda, VPC, IAM, S3, etc.

## Code Organization Principles

**Minimal and Focused**
- Each file has single responsibility
- No unnecessary abstractions
- Code is readable and educational

**Tool Pattern**
- All custom tools use `@tool` decorator
- Tools have clear docstrings
- Tools return strings or structured data
- Tools are self-contained

**Notebook Structure**
- Sequential cells (run top-to-bottom)
- Clear section headers with learning objectives
- Code cells followed by explanation
- Output shows progress and results

**No Hardcoding**
- AWS region auto-detected
- Account ID auto-detected
- Knowledge Base ID from environment
- Model IDs in configuration

## File Naming Conventions

- Notebooks: `lab{N}-{description}.ipynb`
- Python modules: `{purpose}.py` (lowercase, underscores)
- Infrastructure: `{resource-type}.yaml`
- Data files: `{domain}_{type}.{ext}`

## Dependencies and Imports

**Standard Pattern**
```python
from strands import Agent, tool
from strands.models import BedrockModel
import boto3
import sys
sys.path.append('lab_helpers')
from utils import print_section_header
from translation_tools import evaluate_translation_quality
```

**Avoid**
- Relative imports outside of lab_helpers
- Hardcoded paths
- Credentials in code
- Circular dependencies

## Execution Flow

1. User clones repository to SageMaker or local Jupyter
2. Runs `pip install -r requirements.txt`
3. Opens `lab1-basic-translation.ipynb`
4. Runs cells sequentially through all 4 labs
5. Each lab builds on previous concepts
6. Lab 3 and 4 include infrastructure deployment steps

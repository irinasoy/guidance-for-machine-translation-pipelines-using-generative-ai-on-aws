# Technology Stack

## Core Technologies

**Agent Framework**
- Strands Agents SDK - Agent orchestration and tool management
- Strands Agents Tools - Tool decorators and utilities

**AI/ML**
- Amazon Bedrock - LLM access (Claude 3.7 Sonnet)
- Bedrock Knowledge Base - Vector-based terminology lookup
- OpenSearch Serverless - Vector storage for KB

**AWS Services**
- AgentCore Runtime - Production agent deployment
- AgentCore Observability - Monitoring and tracing
- CloudFormation - Infrastructure as Code

**Python Stack**
- Python 3.10+
- boto3 - AWS SDK
- pandas - Data handling
- python-dotenv - Environment configuration

## Key Dependencies

```
strands-agents>=0.1.0
strands-agents-tools>=0.1.0
boto3>=1.34.0
botocore>=1.34.0
pandas>=2.0.0
python-dotenv>=1.0.0
bedrock-agentcore>=0.1.0
bedrock-agentcore-starter-toolkit>=0.1.0
```

## Common Commands

**Setup**
```bash
pip install -r requirements.txt
aws sts get-caller-identity  # Verify AWS credentials
```

**Development**
- Open Jupyter notebooks sequentially: `lab1-basic-translation.ipynb` → `lab4-agentcore-deployment.ipynb`
- Run cells top-to-bottom within each lab
- Each lab is self-contained but builds on previous concepts

**Infrastructure**
```bash
# Deploy Knowledge Base (Lab 3)
aws cloudformation create-stack \
  --stack-name translation-kb \
  --template-body file://infrastructure/knowledge-base.yaml \
  --capabilities CAPABILITY_NAMED_IAM
```

**Deployment**
```bash
# Deploy to AgentCore (Lab 4)
# Uses bedrock-agentcore CLI with lab_helpers/production_agent.py
```

## Model Configuration

**LLM Model**
- Model ID: `us.anthropic.claude-3-7-sonnet-20250219-v1:0`
- Provider: Anthropic Claude 3.7 Sonnet
- Must be enabled in Bedrock console before use

**Knowledge Base**
- Vector search with OpenSearch Serverless
- Data source: CSV with AWS terminology (English-Russian pairs)
- Ingestion time: 5-10 minutes after stack creation

## Architecture Patterns

**Agent Pattern**
```python
from strands import Agent, tool
from strands.models import BedrockModel

@tool
def my_tool(param: str) -> str:
    """Tool description"""
    return result

agent = Agent(
    model=BedrockModel(model_id="..."),
    tools=[my_tool],
    system_prompt="..."
)

result = agent("user message")
```

**Tool Decorator**
- Use `@tool` decorator from `strands` for all custom tools
- Include docstrings with parameter descriptions
- Return strings or structured data
- Tools are automatically discovered by the agent

**Iteration Pattern**
- Agent calls tools to evaluate and refine
- Loop continues until quality threshold met
- Track iteration count via message history
- Implement termination conditions to prevent infinite loops

## Environment Setup

**Required AWS Permissions**
- Bedrock model access (Claude 3.7 Sonnet)
- CloudFormation stack creation
- OpenSearch Serverless resource creation
- IAM role creation
- AgentCore deployment

**AWS Region**
- All resources deployed to same region
- Auto-detected from AWS CLI configuration
- Supported regions: us-east-1, us-west-2, eu-west-1

**Credentials**
- AWS CLI configured with valid credentials
- Credentials passed via boto3 (auto-detected)
- No hardcoded credentials in code

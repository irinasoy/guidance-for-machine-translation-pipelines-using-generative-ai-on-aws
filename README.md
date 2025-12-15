# Intelligent Translation Agent Workshop

Build an AI agent that autonomously improves translation quality through self-evaluation and iteration, demonstrating advanced agentic AI patterns with Amazon Bedrock and Strands Agents.

## 🎯 Workshop Overview

This hands-on workshop teaches you how to build intelligent agents that can evaluate and improve their own work. Using translation as a teaching vehicle, you'll learn core agentic AI patterns that apply to any domain requiring iterative quality improvement.

**What Makes This Different:**
- Agents that self-evaluate and refine their output
- Autonomous iteration until quality thresholds are met
- Integration with authoritative knowledge sources
- Production deployment with full observability

## 🏗️ What You'll Build

A production-quality translation agent that:
1. Translates AWS documentation from English to Russian
2. Evaluates its own translation quality
3. Identifies and fixes issues autonomously
4. Validates terminology against Knowledge Base
5. Iterates until professional quality is achieved
6. Deploys to AgentCore Runtime for production use

## 📚 Labs Overview

### Lab 1: Basic Translation - Understanding the Problem (15 min)
- Create a basic Strands agent with Bedrock
- Perform one-shot translation
- Identify quality issues in machine translation
- Understand why iteration is needed

**Key Pattern:** `Agent(model=BedrockModel(...))`

### Lab 2: Self-Evaluation and Iteration (20 min)
- Build custom evaluation tools
- Implement reflect-refine loops
- Enable agent self-assessment
- Achieve autonomous quality improvement

**Key Pattern:** `@tool` decorator + iteration logic

### Lab 3: Knowledge Base Integration (20 min)
- Deploy Bedrock Knowledge Base with CloudFormation
- Create tools that query authoritative sources
- Validate terminology consistency
- Achieve production-quality output

**Key Pattern:** External knowledge integration

### Lab 4: AgentCore Deployment (25 min)
- Package agent for production
- Deploy to AgentCore Runtime
- Test production endpoints
- Monitor with observability traces

**Key Pattern:** Production deployment + monitoring

## 🚀 Getting Started

### Prerequisites

- AWS account with Bedrock access
- Python 3.10+
- AWS CLI configured
- Claude 3.7 Sonnet enabled in Bedrock
- SageMaker Studio (recommended) or local Jupyter environment

### Quick Setup

1. **Clone this repository to SageMaker Studio:**
   ```bash
   git clone <repository-url>
   cd translation-workshop
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Verify AWS credentials:**
   ```bash
   aws sts get-caller-identity
   ```

4. **Start with Lab 1:**
   Open `lab1-basic-translation.ipynb` and run cells sequentially

## 📁 Repository Structure

```
translation-workshop/
├── lab1-basic-translation.ipynb       # Problem identification
├── lab2-self-evaluation.ipynb         # Iteration patterns
├── lab3-knowledge-base.ipynb          # KB integration
├── lab4-agentcore-deployment.ipynb    # Production deployment
├── lab_helpers/
│   ├── translation_tools.py           # Custom tools
│   ├── utils.py                       # Helper functions
│   └── production_agent.py            # AgentCore entrypoint
├── infrastructure/
│   └── knowledge-base.yaml            # CloudFormation template
├── sample_data/
│   ├── aws_lambda_intro.txt           # Sample AWS doc
│   └── aws_terminology.csv            # Terminology reference
├── requirements.txt                   # Python dependencies
└── README.md                          # This file
```

## 🎓 Learning Objectives

By completing this workshop, you will:

✅ **Master Agentic AI Patterns:**
- Reflect-refine loops for autonomous improvement
- Self-evaluation and quality assessment
- Multi-tool coordination
- External knowledge integration

✅ **Understand Agent Capabilities:**
- When agents add value over simple LLM calls
- How to design quality-driven workflows
- Tool selection and orchestration
- Production deployment considerations

✅ **Gain AWS Skills:**
- Bedrock model integration
- Knowledge Base deployment
- AgentCore Runtime usage
- CloudFormation infrastructure

## 🔑 Key Concepts

### Reflect-Refine Loop
The agent evaluates its output, identifies issues, and refines iteratively:
```
Translate → Evaluate → Refine → Re-evaluate → Repeat until quality >= threshold
```

### Agentic vs Traditional
- **Traditional:** Input → Process → Output (one-shot)
- **Agentic:** Input → Process → Self-Evaluate → Refine → Repeat (iterative)

### Why This Matters
Agents with self-evaluation capabilities can:
- Achieve consistent quality without human intervention
- Adapt to different quality requirements
- Learn from authoritative sources
- Provide transparent reasoning

## 🛠️ Technologies Used

- **Strands Agents SDK** - Agent framework
- **Amazon Bedrock** - Claude 3.7 Sonnet LLM
- **Bedrock Knowledge Base** - Terminology validation
- **AgentCore Runtime** - Production deployment
- **AgentCore Observability** - Monitoring and tracing
- **CloudFormation** - Infrastructure as Code
- **OpenSearch Serverless** - Vector storage

## 📊 Expected Outcomes

After completing the workshop:

1. **Working Agent:** Production-ready translation agent deployed to AgentCore
2. **Quality Improvement:** Measurable improvement from Lab 1 to Lab 4
3. **Reusable Patterns:** Agentic patterns applicable to other domains
4. **AWS Infrastructure:** Deployed KB and AgentCore resources

## 🎯 Use Cases Beyond Translation

The patterns you learn apply to:
- **Code Review:** Iterative code quality improvement
- **Content Generation:** Brand-consistent content creation
- **Data Analysis:** Validated insights with source checking
- **Document Summarization:** Quality-driven summarization
- **Report Generation:** Fact-checked report creation

## 🔍 Troubleshooting

### Common Issues

**Issue:** Bedrock model not accessible
- **Solution:** Enable Claude 3.7 Sonnet in Bedrock console

**Issue:** CloudFormation stack creation fails
- **Solution:** Check IAM permissions for OpenSearch Serverless

**Issue:** Knowledge Base queries return no results
- **Solution:** Wait for data source ingestion to complete (5-10 min)

**Issue:** AgentCore deployment fails
- **Solution:** Verify Docker is running and AWS credentials are configured

## 📚 Additional Resources

- [Strands Agents Documentation](https://strandsagents.com)
- [AgentCore Documentation](https://docs.aws.amazon.com/bedrock-agentcore/)
- [Bedrock Knowledge Bases Guide](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base.html)
- [Agentic AI Patterns](https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-patterns/)

## 🤝 Contributing

This workshop is for educational purposes. Feedback and improvements are welcome!

## 📄 License

This workshop is provided under the MIT License. See LICENSE file for details.

## 🎉 Workshop Complete!

After finishing all labs, you'll have:
- ✅ Built an intelligent, self-improving agent
- ✅ Deployed to production with observability
- ✅ Mastered agentic AI patterns
- ✅ Created reusable infrastructure

**Next Steps:**
- Extend to other language pairs
- Add more quality metrics
- Integrate with CI/CD pipelines
- Apply patterns to your own use cases

---

**Questions or Issues?** Open an issue in this repository or contact the workshop facilitators.

**Happy Building! 🚀**

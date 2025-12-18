Azure Open AI: Production-tested system instructions for enterprise AI agents
# Universal AI Agent Safety Template

> Production-tested system instructions for enterprise AI agents that prioritize accuracy, version-control, and anti-hallucination safeguards.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Azure AI](https://img.shields.io/badge/Azure%20AI-Compatible-0078D4)](https://azure.microsoft.com/en-us/products/ai-services/openai-service)
[![OpenAI](https://img.shields.io/badge/OpenAI-Compatible-412991)](https://platform.openai.com/)

---

## Why This Exists

**The Problem:** Large Language Models hallucinate technical details, mix up software versions, and confidently provide outdated instructions. In technical support, healthcare, legal, and compliance-heavy domains, this is unacceptable and costly.

**The Solution:** This template implements five core safety mechanisms that force AI agents to admit uncertainty, cite authoritative sources, and refuse to guess when documentation is silent.

Designed for real-world deployment in **Azure AI Studio**, **OpenAI Assistants API**, **Anthropic Claude Projects**, and similar agent frameworks.

---

## Key Features

| Problem | Solution |
|---------|----------|
| 🚨 **Hallucinations** | 3-Tier source hierarchy (official docs > blog posts > personal notes) |
| 📅 **Version drift** | Mandatory version validation in every tutorial |
| 🔐 **Security risks** | Tool scoping + PII protection + audit logging |
| ❓ **Scope creep** | Environment clarification rules force specificity |
| ⚖️ **Compliance** | Built-in HIPAA/GDPR/SOC2 escalation protocols |

**Battle-tested:** v1.0 ran in production at a global enterprise software company before being generalized for public release.

---

## Quick Start

### 1. Copy the Template
Download [`TEMPLATE.md`](TEMPLATE.md) or copy the raw markdown into your AI agent's system instructions field.

### 2. Customize Placeholders
Search and replace these brackets with your specific values:

```markdown
[YOUR_DOMAIN]              → "Backup & Disaster Recovery" / "Clinical Protocols" / "Tax Compliance"
[DOMAIN_PRODUCTS]          → "Product A, Product B, Product C"
[DOMAIN_ENVIRONMENTS]      → "VMware vSphere, AWS, Azure, on-premise"
[DOMAIN_TOOLS]             → "PowerShell, REST API, Web Console, Terraform"
[CRITICAL_CONSTRAINT_1]    → "Feature X deprecated in v5.0 (Q3 2025)"
[CRITICAL_CONSTRAINT_2]    → "License Y required for Feature Z"
[INTERNAL_EXPERT_ROLE]     → "Support Team" / "Solutions Architect"
[INTERNAL_SUPPORT_EMAIL]   → "support@yourcompany.com"
[OFFICIAL_TICKET_PROCESS_ID] → "KB-1234"
[CURRENT_YEAR]             → "2025"
[DOMAIN_SPECIFIC_DOCS]     → "Release Notes, API Reference"
```

### 3. Deploy to Your Platform

#### Azure AI Studio / Copilot Studio
1. Navigate to your agent configuration
2. Paste the customized template into the **System Message** field
3. Enable **"On Your Data"** if using indexed content (recommended)
4. Test with version-specific queries

#### OpenAI Assistants API
```python
client.beta.assistants.create(
    name="Technical Support Agent",
    instructions=open("TEMPLATE.md").read(),  # Your customized version
    model="gpt-4-turbo-preview",
    tools=[{"type": "retrieval"}]
)
```

#### Anthropic Claude (Projects)
1. Create a new Project
2. Paste the template into **Custom Instructions**
3. Upload your Tier 1 documentation to the Project knowledge base

### 4. Test Edge Cases
Try these queries to validate behavior:
- ❌ "How do I configure [deprecated_feature]?" → Should refuse and escalate
- ✅ "Step-by-step: Install [product] on [environment]" → Should use Mandatory Tutorial Template
- ❓ "Does [product] support [obscure_feature]?" → Should admit uncertainty if not in Tier 1 docs

---

## Use Cases

### ✅ Technical Support Agents
- **SaaS troubleshooting** (version-specific configurations)
- **Infrastructure runbooks** (Kubernetes, Terraform, cloud platforms)
- **Backup & disaster recovery** (step-by-step restore procedures)

### ✅ Healthcare & Life Sciences
- **Clinical protocol assistants** (evidence-based guidance with source citations)
- **HIPAA-compliant patient care** (PII protection, audit logging)
- **Medical device documentation** (version-controlled instructions)

### ✅ Legal & Compliance
- **Regulatory guidance** (cite-only from official statutes)
- **Contract analysis** (structured comparison templates)
- **Policy documentation** (version-dated references)

### ✅ DevOps & Engineering
- **Incident response playbooks** (atomic steps with checkpoints)
- **Release management** (version-strict deployment procedures)
- **Security remediation** (compliance-aware escalation)

---

## What Makes This Different

Most "prompt templates" are vague platitudes like "be helpful and accurate." This template:

1. **Forces structured output** via the Mandatory Tutorial Template (atomic steps, checkpoints, verification)
2. **Blocks hallucination** via strict source hierarchy (Tier 1 > Tier 2 > Tier 3)
3. **Handles uncertainty** via escalation protocols (admit gaps, don't guess)
4. **Enforces security** via tool scoping and PII protection rules
5. **Maintains version control** by requiring explicit version numbers in every procedure

---

## Example: Before vs. After

### ❌ Without This Template
**User:** "How do I enable backup encryption in v4.0?"  
**Agent:** "Sure! Just go to Settings > Security and toggle 'Enable Encryption.' Make sure you have admin rights."  
*(Hallucinated menu path, no version validation, missing prerequisites)*

### ✅ With This Template
**User:** "How do I enable backup encryption in v4.0?"  
**Agent:**
```markdown
### Enable Backup Encryption in Product X v4.0 ###
**Purpose**: Secure backup data at rest with AES-256 encryption.
**Validated against**: Product X v4.0.2 (Build 4518) – Dec 18, 2025

**Requirements**
- Product X v4.0.2 or later
- Administrator role
- Valid encryption key or certificate
- ⚠️ Warning: Encryption cannot be disabled after initial backup without data loss

**Procedure**
1. Navigate to Settings > Backup Jobs > [Job Name] → expected: Job configuration panel opens
   > ✅ Checkpoint: "Advanced Settings" tab is visible
2. Click "Advanced Settings" → select "Encryption" → expected: Encryption configuration dialog
   [Image: Encryption_Dialog_v4.0]
   🔧 Troubleshooting: If grayed out, verify Administrator role in Access Control

**Verification**
- PowerShell: `Get-BackupJob -Name "JobName" | Select EncryptionEnabled` → should return `True`
- Event ID 1234 in Application log: "Encryption enabled for job [JobName]"
```

---

## Repository Structure

```
├── README.md              ← You are here
├── TEMPLATE.md            ← The full system instructions template
├── examples/
│   └── cloud-infra.md     ← Fully customized example for a cloud infrastructure company
└── LICENSE                ← MIT License
```

---

## Contributing

Issues and PRs are welcome! Focus areas:
- **Domain examples**: Healthcare, legal, finance, manufacturing
- **Integration guides**: AWS Bedrock, Google Vertex AI, LangChain
- **Testing strategies**: Automated validation of instruction adherence
- **Localization**: Non-English versions with cultural/regulatory adjustments

---

## License

MIT License - see [LICENSE](LICENSE) for details.

**TL;DR:** Use this commercially, modify it, share it. Just keep the copyright notice.

---

## Citation

If you use this template in production or research, a link back to this repo is appreciated:

```markdown
AI agent instructions based on the [Universal AI Agent Safety Template](https://github.com/yourusername/ai-agent-safety-template)
```

---

## Version History

- **v1.2** (Dec 2025): Added Azure "on your data" grounding rule, audit logging, normalized formatting
- **v1.1** (Dec 2025): Added Tool & Data Access, Security & Privacy, ethical guardrails
- **v1.0** (Dec 2025): Initial public release, based on production deployment at global enterprise software company

---

**Built with ❤️ for teams who need AI agents that admit when they don't know.**

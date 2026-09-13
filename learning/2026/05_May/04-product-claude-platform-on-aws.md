# Claude Platform on AWS — native platform inside your AWS account

- **Category:** ① Product release
- **Date:** 2026-05-11  ·  **What it affects:** procurement/billing; Claude Platform (API, console, betas) access path
- **Sources:** https://aws.amazon.com/about-aws/whats-new/2026/05/claude-platform-aws/ · https://www.infoq.com/news/2026/05/anthropic-claude-aws/

## In one line
AWS became the first cloud to offer Anthropic's *native* Claude Platform — the same APIs, console, and early-access betas — billed and authenticated through your existing AWS account, rather than the Bedrock-hosted, cloud-managed version of the models.

## What actually changed
This is **not** "Claude on Bedrock." It is the **native Claude Platform**, operated by Anthropic, made reachable through AWS:
- **Access:** Anthropic's APIs, console, and **early-access beta features** through your existing AWS account — no separate Anthropic account, billing, or usage tracking.
- **Included capabilities:** Claude Managed Agents, code execution, web search, web fetch, prompt caching, batch processing, citations, Files API, Skills, and MCP connectors.
- **AWS integration:** authentication via **AWS IAM**, audit logging via **CloudTrail**, billing on a **single AWS invoice**.
- **Feature parity/timing:** Anthropic says new platform and beta features arrive on AWS **at the same time** as on the native Claude API.
- **Caveat:** the platform is operated by Anthropic, and **customer data is processed outside the AWS security boundary** — an important distinction from Bedrock's in-account model hosting.

## Why it matters
Historically, "Claude on AWS" meant Bedrock, which lagged the native platform on newest features and betas and wrapped the models in AWS's own surface. This closes that gap for the *platform*: AWS customers get day-one access to Managed Agents, Skills, betas, etc., while keeping IAM/CloudTrail/consolidated billing. The tradeoff is the data-boundary caveat — convenience of AWS-native procurement, but data leaves the AWS security boundary because Anthropic operates it.

## Your point of view
- "The value here is procurement and parity, not new model capability: day-one betas plus IAM/CloudTrail/one invoice removes the main reason enterprises tolerated Bedrock's feature lag."
- "Read the fine print: this is Anthropic-operated, data processed outside the AWS boundary — so it's not a substitute for Bedrock when in-account data residency is the requirement."
- "Choose deliberately: native platform on AWS for latest features and simple billing; Bedrock when you need AWS to hold the data boundary."

## What to do
- If you're an AWS shop already on Bedrock for the feature set, evaluate switching to Claude Platform on AWS to get betas/Managed Agents/Skills day one under IAM + consolidated billing.
- Run the data-boundary caveat past security/compliance before migrating regulated workloads; keep Bedrock where in-account processing is mandatory.

## Connects to
- [build vs buy](../../../product-strategy/build-vs-buy.md) · [production architecture](../../../production-ops/production-architecture.md) · [API endpoint](../../../dev-surfaces/api-endpoint.md) · [AI security](../../../safety-trust/ai-security.md)

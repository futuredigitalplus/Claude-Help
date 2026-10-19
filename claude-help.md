# Best Way Claude

Plugin commands for Claude Code on Mac and Windows. Every line runs the same in macOS Terminal, Windows PowerShell and Cursor's terminal unless marked otherwise.

Restart `claude` after any change.

## 1. Common plugins (user scope, every project)

```text
claude plugin marketplace add anthropics/claude-plugins-official
claude plugin install superpowers@claude-plugins-official --scope user
claude plugin install github@claude-plugins-official --scope user
claude plugin install commit-commands@claude-plugins-official --scope user
claude plugin install code-review@claude-plugins-official --scope user
claude plugin install feature-dev@claude-plugins-official --scope user
claude plugin install context7@claude-plugins-official --scope user
claude plugin install security-guidance@claude-plugins-official --scope user
claude plugin install claude-md-management@claude-plugins-official --scope user
claude plugin install session-report@claude-plugins-official --scope user
```

## 2. Project scope

Open the terminal **in the project's root folder** first.

### Unity game

```text
claude plugin install unity@claude-plugins-official --scope project
claude plugin install csharp-lsp@claude-plugins-official --scope project
```

Only if the game uses them:

```text
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install revenuecat@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

If `unity` is already in the project but disabled:

```text
claude plugin enable unity@claude-plugins-official --scope project
```

### Next.js

```text
claude plugin install frontend-design@claude-plugins-official --scope project
claude plugin install typescript-lsp@claude-plugins-official --scope project
claude plugin install playwright@claude-plugins-official --scope project
```

Only if the app uses them:

```text
claude plugin install vercel@claude-plugins-official --scope project
claude plugin install supabase@claude-plugins-official --scope project
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install stripe@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

### FastAPI

```text
claude plugin install pyright-lsp@claude-plugins-official --scope project
```

Only if the API uses them:

```text
claude plugin install logfire@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
claude plugin install supabase@claude-plugins-official --scope project
claude plugin install firebase@claude-plugins-official --scope project
```

### iOS (Swift / SwiftUI)

```text
claude plugin install swift-lsp@claude-plugins-official --scope project
```

Only if the app uses them:

```text
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install revenuecat@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

### React Native

```text
claude plugin install typescript-lsp@claude-plugins-official --scope project
```

Only if the app uses them:

```text
claude plugin install expo@claude-plugins-official --scope project
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install supabase@claude-plugins-official --scope project
claude plugin install revenuecat@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

### Flutter

There is no Dart or Flutter language plugin in the official marketplace. `context7` at user scope covers the Flutter and Dart docs.

Only if the app uses them:

```text
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install revenuecat@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

### Android Studio (Kotlin / Java)

```text
claude plugin install kotlin-lsp@claude-plugins-official --scope project
```

For Java code, add:

```text
claude plugin install jdtls-lsp@claude-plugins-official --scope project
```

Only if the app uses them:

```text
claude plugin install firebase@claude-plugins-official --scope project
claude plugin install revenuecat@claude-plugins-official --scope project
claude plugin install sentry@claude-plugins-official --scope project
```

## 3. Check

```text
claude plugin list
claude plugin marketplace list
claude plugin details <name>@claude-plugins-official
```

Inside `claude`:

```text
/context
```

Find which projects have project-scope plugins:

macOS:

```bash
grep '"projectPath"' ~/.claude/plugins/installed_plugins.json
```

Windows PowerShell:

```powershell
Select-String -Path "$env:USERPROFILE\.claude\plugins\installed_plugins.json" -Pattern '"projectPath"'
```

## 4. Remove

From user scope:

```text
claude plugin uninstall <name>@claude-plugins-official
```

From a project (run inside that project folder):

```text
claude plugin uninstall <name>@claude-plugins-official --scope project
```

Turn off without removing, and turn back on:

```text
claude plugin disable <name>@claude-plugins-official
claude plugin enable <name>@claude-plugins-official
```

## 5. Set effort level

macOS, set to medium:

```bash
sed -i '' 's/"effortLevel": "high"/"effortLevel": "medium"/g' ~/.claude/settings.json
```

Windows PowerShell, set to medium:

```powershell
(Get-Content "$env:USERPROFILE\.claude\settings.json" -Raw) -replace '"effortLevel": "high"','"effortLevel": "medium"' | Set-Content "$env:USERPROFILE\.claude\settings.json" -NoNewline
```

For one session only, inside `claude`:

```text
/effort high
```

## 6. Plugin help links

Read a plugin's page to check its features before you install it. You can also see what a plugin adds from the terminal:

```text
claude plugin details <name>@claude-plugins-official
```

### Common plugins

| Plugin | Help page |
|---|---|
| `superpowers` | https://github.com/obra/superpowers |
| `github` | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/github |
| `commit-commands` | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/commit-commands |
| `code-review` | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/code-review |
| `feature-dev` | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/feature-dev |
| `context7` | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/context7 |
| `security-guidance` | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/security-guidance |
| `claude-md-management` | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-md-management |
| `session-report` | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/session-report |

### Project plugins

| Plugin | Used in | Help page |
|---|---|---|
| `unity` | Unity | https://github.com/Unity-Technologies/unity-agent-plugin |
| `csharp-lsp` | Unity | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/csharp-lsp |
| `frontend-design` | Next.js | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/frontend-design |
| `typescript-lsp` | Next.js, React Native | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/typescript-lsp |
| `playwright` | Next.js | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/playwright |
| `vercel` | Next.js | https://github.com/vercel/vercel-plugin |
| `pyright-lsp` | FastAPI | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/pyright-lsp |
| `logfire` | FastAPI | https://github.com/pydantic/skills/tree/main/plugins/logfire |
| `swift-lsp` | iOS | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/swift-lsp |
| `expo` | React Native | https://github.com/expo/skills/blob/main/plugins/expo/README.md |
| `kotlin-lsp` | Android | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/kotlin-lsp |
| `jdtls-lsp` | Android (Java) | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/jdtls-lsp |
| `firebase` | Any | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/firebase |
| `supabase` | Any | https://github.com/supabase-community/supabase-plugin |
| `stripe` | Web | https://github.com/stripe/ai/tree/main/providers/claude/plugin |
| `revenuecat` | Mobile, Unity | https://github.com/RevenueCat/rc-claude-code-plugin |
| `sentry` | Any | https://github.com/getsentry/plugin-claude |

Browse every official plugin: https://github.com/anthropics/claude-plugins-official

## 7. Full official plugin catalog

Every plugin in `claude-plugins-official` (315 plugins), grouped by category. Install any of them with:

```text
claude plugin install <name>@claude-plugins-official --scope project
```

Use `--scope user` only for plugins every project needs.

### Development (123)

| Plugin | What it does | Help page |
|---|---|---|
| `agent-sdk-dev` | Development kit for working with the Claude Agent SDK | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/agent-sdk-dev |
| `agentforce-adlc` | Agentforce Agent Development Life Cycle — author, discover, scaffold, deploy, test, and optimize .agent files | https://github.com/SalesforceAIResearch/agentforce-adlc |
| `airwallex-dev` | Build Airwallex payment integrations in your own codebase. Generates the checkout, card-element, onboarding, and subscription-billing… | https://www.airwallex.com/docs |
| `amd-skills` | AMD's verified Agent Skills in one plugin: route image/audio through local AI on Ryzen AI, serve LLMs on AMD Instinct GPUs with vLLM,… | https://developer.amd.com/ |
| `apollo-skills` | Apollo GraphQL agent skills for Claude Code — Apollo Client, Server, Federation, Connectors, Router, Rover CLI, iOS, Kotlin, and the… | https://www.apollographql.com |
| `appwrite` | Appwrite tools for Claude Code, including SDK skills, Appwrite MCP servers, and deployment commands. | https://appwrite.io |
| `astronomer-data-agents` | Data engineering for Apache Airflow and Astronomer. Author DAGs with best practices, debug pipeline failures, trace data lineage,… | https://github.com/astronomer/agents |
| `atomic-agents` | Comprehensive development workflow for building AI agents with the Atomic Agents framework. Includes specialized agents for schema… | https://github.com/BrainBlend-AI/atomic-agents |
| `aws-agents` | Build, deploy, and operate AI agents on AWS. Skills for scaffolding agents with Amazon Bedrock AgentCore, connecting tools, memory,… | https://github.com/aws/agent-toolkit-for-aws |
| `aws-agents-for-devsecops` | Investigate incidents, review code and execute UAT for release readiness, scan code for vulnerabilities, and run penetration tests with… | https://github.com/aws/agent-toolkit-for-aws |
| `aws-amplify` | Build full-stack apps with AWS Amplify Gen 2 using guided workflows for authentication, data models, storage, GraphQL APIs, and Lambda… | https://github.com/awslabs/agent-plugins |
| `aws-core` | Build, deploy, and operate applications on AWS. Skills to author infrastructure-as-code, use core services, and complete common tasks. | https://github.com/aws/agent-toolkit-for-aws |
| `aws-data-analytics` | Data lake, analytics, and ETL workflows with S3 Tables, AWS Glue, and Athena. | https://github.com/aws/agent-toolkit-for-aws |
| `aws-serverless` | Design, build, deploy, test, and debug serverless applications with AWS Serverless services. | https://github.com/awslabs/agent-plugins |
| `aws-startup-advisor` | Personalized AWS guidance built on patterns from 350,000+ startups. Get architecture, cost, and security recommendations matched to your… | https://github.com/aws/agent-toolkit-for-aws |
| `base44` | Build and deploy Base44 full-stack apps with CLI project management and JavaScript/TypeScript SDK development skills | https://docs.base44.com |
| `boltz` | Predict structures, screen molecules and proteins, and design binders with Boltz from Claude Code. | https://boltz.bio |
| `buildkite` | Official Buildkite skills for Claude Code, Cursor, and other AI coding agents — pipelines, migration, preflight, agent runtime, CLI, and API | https://buildkite.com |
| `catalyst-by-zoho` | Official Claude Code plugin for Catalyst by Zoho — full-stack serverless cloud platform. With Skills that covers all services, SDKs,… | https://catalyst.zoho.com/ |
| `cds-mcp` | AI-assisted development of SAP Cloud Application Programming Model (CAP) projects. Search CDS models and CAP documentation. | https://cap.cloud.sap/ |
| `chrome-devtools-mcp` | Control and inspect a live Chrome browser from your coding agent. Record performance traces, analyze network requests, check console… | https://github.com/ChromeDevTools/chrome-devtools-mcp |
| `circle-skills` | Ship stablecoin apps faster. Best-practice skills for USDC payments, cross-chain transfers, wallets, and smart contracts — plus Circle's… | https://www.circle.com |
| `ckeditor` | Install, configure, and integrate CKEditor 5 (free and premium) in any JavaScript project. | https://ckeditor.com |
| `clangd-lsp` | C/C++ language server (clangd) for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/clangd-lsp |
| `code-modernization` | Guided modernization for any legacy codebase: start with /modernize, get an assessment, an interactive map, the business rules mined… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-modernization |
| `codspeed` | CodSpeed is the all-in-one performance testing toolkit. Dive into benchmarking results, flamegraphs, and performance comparisons — give… | https://codspeed.io |
| `confidence` | Access Confidence feature flags, experiments, and migration tools directly from Claude Code. | https://confidence.spotify.com |
| `context7` | Upstash Context7 MCP server for up-to-date documentation lookup. Connects to Context7's hosted remote MCP server… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/context7 |
| `csharp-lsp` | C# language server for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/csharp-lsp |
| `data` | Data engineering for Apache Airflow and Astronomer. Author DAGs with best practices, debug pipeline failures, trace data lineage,… | https://github.com/astronomer/agents |
| `data-agent-kit` | This plugin provides a specialized suite of skills for data engineers and database practitioners working on Google Cloud. It acts as an… | https://cloud.google.com/products/data-agent-kit |
| `datarobot-agent-skills` | DataRobot skills for AI/ML workflows — model training, deployment, predictions, feature engineering, monitoring, explainability, data… | https://datarobot.com |
| `deepeval` | Skills for adding DeepEval evaluations, tracing, datasets, Confident AI reports, and iterative improvement loops to AI applications. | https://github.com/confident-ai/deepeval |
| `dominodatalab` | Full Domino Data Lab platform support — workspaces, jobs, model deployment, experiment tracking, GenAI tracing, Spark/Ray/Dask, and app… | https://www.domino.ai |
| `expo` | Official Expo skills for building, deploying, upgrading, and debugging React Native apps with Expo. Covers UI development with Expo… | https://github.com/expo/skills/blob/main/plugins/expo/README.md |
| `fakechat` | Localhost web chat for testing the channel notification flow. No tokens, no access control, no third-party service. | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/fakechat |
| `feature-dev` | Comprehensive feature development workflow with specialized agents for codebase exploration, architecture design, and quality review | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/feature-dev |
| `firecrawl` | Web scraping and crawling powered by Firecrawl. Turn any website into clean, LLM-ready markdown or structured data. Scrape single pages,… | https://github.com/firecrawl/firecrawl-claude-plugin |
| `forge-skills` | Forge-focused skills and MCP configuration for Atlassian Forge: scaffold and deploy apps (forge create, templates, dev spaces), build… | https://developer.atlassian.com/platform/forge/ |
| `frontend-design` | Create distinctive, production-grade frontend interfaces with high design quality. Generates creative, polished code that avoids generic… | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/frontend-design |
| `gitkraken` | Gives Claude access to your real Git and project context: commits, branches, pull requests, and issues across every repo you work in.… | https://www.gitkraken.com |
| `gopls-lsp` | Go language server for code intelligence and refactoring | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/gopls-lsp |
| `greptile` | AI code review agent for GitHub and GitLab. View and resolve Greptile's PR review comments, run reviews on your working branch, and… | https://www.greptile.com/docs/mcp-v2/overview |
| `huggingface-skills` | Build, train, evaluate, and use open source AI models, datasets, and spaces. | https://github.com/huggingface/skills |
| `idmp-plugin` | TDengine IDMP plugin with packaged skills for discovery, schema inspection, and safe operational workflows. | https://github.com/taosdata/agent-skills |
| `jdtls-lsp` | Java language server (Eclipse JDT.LS) for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/jdtls-lsp |
| `kotlin-lsp` | Kotlin language server for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/kotlin-lsp |
| `laravel-boost` | Laravel development toolkit MCP server. Provides intelligent assistance for Laravel applications including Artisan commands, Eloquent… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/laravel-boost |
| `liquid-lsp` | LSP integration for Shopify Liquid templates via the Shopify CLI theme language server. | https://github.com/Shopify/liquid-skills/tree/main/plugins/liquid-lsp |
| `liquid-skills` | Liquid language fundamentals, CSS/JS/HTML coding standards, and WCAG accessibility patterns for Shopify themes | https://github.com/Shopify/liquid-skills/tree/main/plugins/liquid-skills |
| `lovable` | Build, iterate on, deploy, and manage Lovable apps from Claude Code. Bundles the official Lovable MCP server (remote, OAuth 2.1) and… | https://lovable.dev |
| `lua-lsp` | Lua language server for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/lua-lsp |
| `lumen` | Precise local semantic code search via MCP. Indexes your codebase with Go AST parsing, embeds with Ollama or LM Studio, and exposes… | https://www.ory.sh |
| `mattpocock-skills` | Matt Pocock's agent skills for real engineering — grilling, spec/ticket flows, TDD, code review, domain modelling and more.… | https://github.com/mattpocock/skills |
| `mcp-apps` | Skills for creating MCP Apps with the MCP Apps SDK | https://modelcontextprotocol.io |
| `mcp-server-dev` | Skills for designing and building MCP servers that work seamlessly with Claude. Guides you through deployment models (remote HTTP, MCPB,… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/mcp-server-dev |
| `mcp-tunnels` | Connect Claude to a private MCP server through an Anthropic MCP tunnel. The /create-docker-mcp-tunnel command drives the Docker Compose… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/mcp-tunnels |
| `mercadopago` | Mercado Pago full-product integration toolkit. One agent routes to four orchestration skills (mp-integrate wizard, mp-webhooks,… | https://github.com/mercadopago/mercadopago-claude-marketplace/tree/main/plugins/mercadopago |
| `mergify` | Skills for the Mergify CLI: manage merge queues, stacked pull requests, Test Insights (flaky tests, quarantine), merge protections, and… | https://mergify.com |
| `microsoft-docs` | Access official Microsoft documentation, API references, and code samples for Azure, .NET, Windows, and more. | https://github.com/microsoftdocs/mcp |
| `migration-to-aws` | Plan a migration from Google Cloud Platform (and OpenAI/Gemini AI workloads) to AWS. Analyzes your Infrastructure-as-Code files, app… | https://github.com/awslabs/startups |
| `mintlify` | Build beautiful documentation sites with Mintlify. Convert non-markdown files into properly formatted MDX pages, add and modify content… | https://www.mintlify.com/ |
| `modern-web-guidance` | Keep your coding agent up to date with the latest web best practices | https://goo.gle/modern-web-guidance |
| `netlify-skills` | Netlify platform skills for Claude Code — functions, edge functions, blobs, database, image CDN, forms, config, CLI, frameworks,… | https://github.com/netlify/context-and-tools |
| `netsuite-suitecloud` | Develop NetSuite SuiteCloud solutions with SuiteScript, SDF, and best practices: SuiteScript records and upgrades, SDF objects, roles… | https://github.com/oracle/netsuite-suitecloud-sdk/tree/ai-plugins-dist/anthropic/netsuite-suitecloud |
| `nvidia-skills` | Find the right NVIDIA skill for GPU acceleration, CUDA, AI agents, data loading, training, inference, robotics, Physical AI, Omniverse,… | https://build.nvidia.com/skills/ |
| `oracle-ai-data-platform-workbench-databricks-migrator` | Drive the Oracle AI Data Platform (AIDP) Databricks Migration Toolkit in natural language. Plans and executes automated Databricks →… | https://docs.oracle.com/en/cloud/paas/ai-data-platform/index.html |
| `oracle-ai-data-platform-workbench-engineer-agent` | Oracle AI Data Platform (AIDP) Workbench engineer agent for Claude Code — a 37-skill agent that operates the full Spark/Delta lakehouse… | https://docs.oracle.com/en/cloud/paas/ai-data-platform/index.html |
| `oracle-ai-data-platform-workbench-spark-connectors` | Oracle AI Data Platform Workbench Spark connectors for Claude Code. 18 connector skills covering every data source workbench customers… | https://docs.oracle.com/en/cloud/paas/ai-data-platform/index.html |
| `outputai` | Output.ai workflow development toolkit for Claude Code. Adds 5 specialist agents (planner, builder, debugger, prompt writer, quality… | https://output.ai |
| `paypal` | PayPal development plugin for Claude — integrate payments, subscriptions, invoices, disputes, and more using PayPal's APIs and MCP server | https://developer.paypal.com/ |
| `php-lsp` | PHP language server (Intelephense) for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/php-lsp |
| `pixeltable` | Build multimodal AI applications with Pixeltable -- tables, computed columns, embedding search, UDFs, tool-calling agents, and 25+ AI… | https://docs.pixeltable.com |
| `playground` | Creates interactive HTML playgrounds — self-contained single-file explorers with visual controls, live preview, and prompt output with… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/playground |
| `plugin-dev` | Comprehensive toolkit for developing Claude Code plugins. Includes 7 expert skills covering hooks, MCP integration, commands, agents,… | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/plugin-dev |
| `postman` | Work with Postman from your agent: bootstrap a repo's Postman setup, mock an API before it's implemented, run collection and governance… | https://github.com/postmanlabs/postman-plugin |
| `preset-cli-skills` | Preset CLI skills for explicit shell, scripting, and CI/CD workflows driven by the `sup` CLI (PyPI package `superset-sup`). Use only for… | https://www.preset.io |
| `pydantic-ai` | Write accurate Pydantic AI code from the start. Up-to-date patterns, decision trees, and common gotchas for agents, tools, structured… | https://github.com/pydantic/skills/tree/main/plugins/ai |
| `pyright-lsp` | Python language server (Pyright) for type checking and code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/pyright-lsp |
| `qodo` | Bring Qodo's codebase intelligence, coding standards, and code review into your coding agent. | https://github.com/qodo-ai/qodo-skills |
| `qodo-standards` | Optional Qodo rules discovery and standards administration workflows. | https://github.com/qodo-ai/qodo-skills |
| `qt-development-skills` | Agentic engineering skills for Qt software development — Qt C++/QML code review, QML coding, and Qt C++/QML code documentation. | https://www.qt.io/ |
| `quarkus-agent` | MCP server for AI coding agents to create, manage, and interact with Quarkus applications. Provides tools for project scaffolding, dev… | https://quarkus.io |
| `ralph-loop` | Interactive self-referential AI loops for iterative development, implementing the Ralph Wiggum technique. Claude works on the same task… | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/ralph-loop |
| `rc` | Configure RevenueCat projects, apps, products, entitlements, and offerings directly from Claude Code. Manage your in-app purchase… | https://www.revenuecat.com |
| `resend` | Agent skills for working with Resend to send and receive emails — email API integration, agent inbox, CLI, React Email components, and… | https://resend.com |
| `revenuecat` | Configure RevenueCat projects, apps, products, entitlements, and offerings directly from Claude Code. Manage your in-app purchase… | https://www.revenuecat.com |
| `rill` | Skills for developing and querying projects in the Rill business intelligence platform | https://docs.rilldata.com/developers/build/ai-configuration |
| `ruby-lsp` | Ruby language server for code intelligence and analysis | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/ruby-lsp |
| `rust-analyzer-lsp` | Rust language server for code intelligence and analysis | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/rust-analyzer-lsp |
| `sagemaker-ai` | Build, train, and deploy AI models with deep AWS AI/ML expertise brought directly into your coding assistants, covering the surface area… | https://github.com/awslabs/agent-plugins |
| `salesforce-development` | Build Salesforce apps and agents using these core building blocks: metadata, Apex, deploy/retrieve, security, reporting, and generated… | https://github.com/forcedotcom/sf-skills/tree/main/plugins/builder/salesforce-development |
| `sanity` | Sanity content platform integration with MCP server, agent skills, and slash commands. Query and author content, build and optimize GROQ… | https://www.sanity.io |
| `sap-cds-mcp` | AI-assisted development of SAP Cloud Application Programming Model (CAP) projects. Search CDS models and CAP documentation. | https://cap.cloud.sap/ |
| `sap-fiori-mcp-server` | MCP server for SAP Fiori development tools for Claude Code. Build and modify SAP Fiori applications with AI assistance. | https://github.com/SAP/open-ux-tools/tree/main/packages/fiori-mcp-server |
| `sap-mdk-server` | MCP server for SAP Mobile Development Kit (MDK). Build and modify MDK applications with AI assistance — schema lookups, action… | https://help.sap.com/docs/MDK |
| `scandit-sdk` | AI agent skills for integrating the Scandit Data Capture SDK — product selection, documentation, and implementation guides for barcode… | https://www.scandit.com |
| `serena` | Semantic code analysis MCP server providing intelligent code understanding, refactoring suggestions, and codebase navigation through… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/serena |
| `servicenow-sdk` | Create, edit, and deploy ServiceNow applications with the Fluent SDK effortlessly through Claude AI. | https://servicenow.github.io/sdk/ |
| `setup-agent-analytics` | Detect AI agents in your codebase and instrument them with Pendo Agent Analytics via the best-fit path: Python SDK, TypeScript SDK,… | https://github.com/pendo-io/claude-pendo-plugin/tree/main/plugins/setup-agent-analytics |
| `setup-mcp-agent-analytics` | Detect an MCP server's language (Python, TypeScript or Go) and instrument it with the matching Pendo SDK so MCP tool calls flow into… | https://github.com/pendo-io/claude-pendo-plugin/tree/main/plugins/setup-mcp-agent-analytics |
| `shopify-ai-toolkit` | Shopify's AI Toolkit provides 18 development skills for building on the Shopify platform, covering documentation search, API schema… | https://shopify.dev |
| `skill-creator` | Create new skills, improve existing skills, and measure skill performance. Use when users want to create a skill from scratch, update or… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/skill-creator |
| `snowflake-cortex-code` | Automatically route Snowflake prompts from Claude Code to Cortex Code for execution. Provides slash commands for code review and task… | https://docs.snowflake.com/en/user-guide/cortex-code |
| `sourcegraph` | Code search and understanding across codebases. Search, read, and trace references across repositories; analyze refactor impact;… | https://sourcegraph.com |
| `streaming-skills-plugin` | Skills for streaming application developers, covering Kafka and Flink client libraries and Schema Registry | https://www.confluent.io |
| `stripe` | Stripe development plugin for Claude | https://github.com/stripe/ai/tree/main/providers/claude/plugin |
| `sumup` | SumUp payment integrations across terminal and online checkout flows. Build Android and iOS POS apps with SumUp card readers, online… | https://www.sumup.com/ |
| `superpowers` | Superpowers teaches Claude brainstorming, subagent driven development with built in code review, systematic debugging, and red/green… | https://github.com/obra/superpowers |
| `swift-lsp` | Swift language server (SourceKit-LSP) for code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/swift-lsp |
| `tavily` | Build AI applications with real-time web data using Tavily's search, extract, crawl, and research APIs. | https://www.tavily.com/ |
| `teamcity-cli` | Agent skill for interacting with TeamCity CI/CD using the teamcity CLI. Enables Claude to explore builds, view logs, start jobs, manage… | https://www.jetbrains.com/teamcity/ |
| `terraform` | The Terraform MCP Server provides seamless integration with Terraform ecosystem, enabling advanced automation and interaction… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/terraform |
| `togetherai-skills` | Agent Skills for Together AI platform — inference, training, embeddings, audio, video, images, function calling, and infrastructure.… | https://www.together.ai |
| `twilio-developer-kit` | Twilio Skills provide procedural knowledge for AI coding agents — which APIs to use, in what order, and what to avoid. Covers SMS,… | https://www.twilio.com |
| `typescript-lsp` | TypeScript/JavaScript language server for enhanced code intelligence | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/typescript-lsp |
| `ui5` | SAPUI5 / OpenUI5 plugin for coding agents. Create and validate UI5 projects, access API documentation, run UI5 linter, get development… | https://github.com/UI5/plugins-coding-agents |
| `ui5-modernization` | Complete UI5 modernization toolkit with workflow and specialized fix patterns for modernizing SAPUI5/OpenUI5 applications. | https://github.com/UI5/plugins-coding-agents |
| `ui5-typescript-conversion` | SAPUI5 / OpenUI5 plugin for coding agents. Convert JavaScript based UI5 projects to TypeScript. | https://github.com/UI5/plugins-coding-agents |
| `unity` | Unity's official plugin for Claude Code, with curated skills for game development, monetization, and performance optimization. | https://unity.com |
| `unreal-engine-skills-for-claude-code` | Control Unreal Editor directly from Claude Code via MCP. Hundreds of tools exposed via Unreal's ToolsetRegistry across 30+ toolsets:… | https://dev.epicgames.com/documentation/unreal-engine/unreal-mcp-in-unreal-editor |
| `wix` | Build, manage, and deploy Wix sites and apps. CLI development skills for dashboard extensions, backend APIs, site widgets, and service… | https://dev.wix.com/docs/wix-cli/guides/development/about-wix-skills |
| `zoom-plugin` | Claude plugin for planning, building, and debugging Zoom integrations across REST APIs, SDKs, webhooks, bots, and MCP workflows. | https://developers.zoom.us/ |

### Database (39)

| Plugin | What it does | Help page |
|---|---|---|
| `aiven` | Easily deploy managed PostgreSQL (pg), Kafka, OpenSearch, Clickhouse and other databases, streaming and apps. Free tier available, up… | https://aiven.io |
| `alloydb` | Create, connect, and interact with an AlloyDB for PostgreSQL database and data. | https://cloud.google.com/alloydb |
| `alloydb-omni` | Create, connect, and interact with an AlloyDB Omni database and data. | https://github.com/gemini-cli-extensions/alloydb-omni |
| `altimate-code` | Delegates dbt and warehouse work to altimate-code, a specialized CLI agent with 100+ purpose-built data tools (SQL analysis,… | https://www.altimate.ai |
| `azure-cosmos-db-assistant` | Expert assistant for Azure Cosmos DB — data modeling, query optimization, performance tuning, and best practices. | https://github.com/AzureCosmosDB/cosmosdb-claude-code-plugin |
| `azure-sql-developer` | Agent skills for Azure SQL Developer, the Azure SQL Database engine running locally in a container. Teaches your agent to run the… | https://github.com/microsoft/azure-sql-database-container |
| `bigdata-com` | Official Bigdata.com plugin providing financial research, analytics, and intelligence tools powered by Bigdata MCP. | https://docs.bigdata.com |
| `bigquery-data-analytics` | Connect, query, and generate data insights for BigQuery datasets and data. | https://github.com/gemini-cli-extensions/bigquery-data-analytics |
| `clickhouse` | Connect Claude to your ClickHouse Cloud databases. Browse organizations, services, databases, and table schemas. Run read-only SQL… | https://github.com/ClickHouse/clickhouse-claude-code-plugin |
| `clickhouse-best-practices` | 28 best practice rules for ClickHouse schema design, query optimization, and data ingestion — prioritized by impact | https://clickhouse.com |
| `cloud-sql-mysql` | Connect and interact with a Cloud SQL for MySQL database and data. | https://github.com/gemini-cli-extensions/cloud-sql-mysql |
| `cloud-sql-postgresql` | Create, connect, and interact with a Cloud SQL for PostgreSQL database and data. | https://cloud.google.com/sql |
| `cloud-sql-sqlserver` | Connect to Cloud SQL for SQL Server | https://github.com/gemini-cli-extensions/cloud-sql-sqlserver |
| `cockroachdb` | Connect Claude Code directly to your CockroachDB clusters for hands-on database work — explore schemas, write optimized SQL, debug… | https://github.com/cockroachdb/claude-plugin |
| `convex` | Official Convex plugin for Claude Code with bundled Convex skills, the convex-expert subagent for code-writing, a runtime-error monitor,… | https://github.com/get-convex/convex-backend-skill |
| `databases-on-aws` | Expert database guidance for the AWS database portfolio. Design schemas, execute queries, handle migrations, and choose the right… | https://github.com/awslabs/agent-plugins |
| `databricks` | Databricks skills for the CLI, Apps, Lakebase, Model Serving, Lakeflow Jobs, Spark Declarative Pipelines, Declarative Automation Bundles… | https://developers.databricks.com/ |
| `datahub-skills` | DataHub development and interaction toolkit with connector planning, PR review, catalog search, metadata enrichment, lineage tracing,… | https://datahub.com |
| `dataproc` | Manage Dataproc clusters and jobs. | https://github.com/gemini-cli-extensions/dataproc |
| `dataverse` | Agent skills for building on, analyzing, and managing Microsoft Dataverse — with Dataverse MCP, PAC CLI, and Python SDK. | https://github.com/microsoft/Dataverse-skills |
| `duckdb-skills` | DuckDB-powered skills for Claude Code: read any data file, attach and query DuckDB databases, search DuckDB/DuckLake docs, search past… | https://duckdb.org |
| `firebase` | Google Firebase MCP integration. Manage Firestore databases, authentication, cloud functions, hosting, and storage. Build and manage… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/firebase |
| `firestore-native` | Connect and interact with Firestore databases, collections, and documents. | https://github.com/gemini-cli-extensions/firestore-native |
| `informatica-for-claude-platform` | Governed catalog discovery for Informatica Intelligent Data Management Cloud (CDGC): find tables, columns, files, glossary terms and… | https://github.com/forcedotcom/informatica-claude-plugins/tree/main/informatica-for-claude-platform |
| `knowledge-catalog` | Connect to Knowledge Catalog to discover, manage, monitor, and govern data and AI artifacts across your data platform | https://github.com/gemini-cli-extensions/knowledge-catalog |
| `looker` | Connect to Looker and interact with your data using LookML. | https://github.com/gemini-cli-extensions/looker |
| `mongodb` | Official Claude plugin for MongoDB (MCP Server + Skills). Connect to databases, explore data, manage collections, optimize queries,… | https://www.mongodb.com/docs/mcp-server/overview/ |
| `mongodb-atlas` | Connect to MongoDB Atlas clusters only through the Atlas Managed MCP Server. Sign in with your Atlas account to explore data, manage… | https://www.mongodb.com/docs/mcp-server/get-started/ |
| `neon` | Manage your Neon projects and databases with the neon-postgres agent skill and the Neon MCP Server. | https://github.com/neondatabase/agent-skills/tree/main/plugins/neon-postgres |
| `oracledb` | Connect, query, and interact with Oracle Databases and their data. | https://github.com/gemini-cli-extensions/oracledb |
| `pinecone` | Pinecone vector database integration. Streamline your Pinecone development with powerful tools for managing vector indexes, querying… | https://github.com/pinecone-io/pinecone-claude-code-plugin |
| `planetscale` | An authenticated hosted MCP server that accesses your PlanetScale organizations, databases, branches, schema, and Insights data. Query… | https://planetscale.com/ |
| `qdrant-skills` | Agent skills for Qdrant vector search covering scaling, performance optimization, search quality, monitoring, deployment, model… | https://skills.qdrant.tech |
| `redis-development` | Redis development best practices — data structures, query engine, vector search, caching, and performance optimization | https://redis.io |
| `sap-hana-cli` | 150+ SAP HANA database tools for AI assistants. Query tables, import/export data, profile data quality, compare schemas, manage backups,… | https://github.com/SAP-samples/hana-cli-claude-plugin |
| `spanner` | Connect and interact with Spanner data using natural language. | https://github.com/gemini-cli-extensions/spanner |
| `supabase` | Supabase MCP integration for database operations, authentication, storage, and real-time subscriptions. Manage your Supabase projects,… | https://github.com/supabase-community/supabase-plugin |
| `vsql-extension-builder` | Builds a VillageSQL extension for MySQL end-to-end through a 7-phase persona-driven workflow. Commonly used to port PostgreSQL… | https://villagesql.com |
| `zilliz` | Zilliz Cloud management plugin with 14 skills covering cluster lifecycle, collection schema, vector search, index tuning, bulk import,… | https://docs.zilliz.com |

### Deployment (9)

| Plugin | What it does | Help page |
|---|---|---|
| `azure` | Transform Claude into an Azure expert. This plugin integrates the Azure MCP server and specialized Azure skills to move beyond generic… | https://github.com/microsoft/azure-skills |
| `cloudflare` | Skills for the Cloudflare developer platform: Workers, Durable Objects, Agents SDK, MCP servers, Wrangler CLI, and web performance. | https://github.com/cloudflare/skills |
| `deploy-on-aws` | Deploy applications to AWS with architecture recommendations, cost estimates, and IaC deployment. | https://github.com/awslabs/agent-plugins |
| `google-cloud-storage` | Official Google Cloud Storage (GCS) plugin. Manage buckets and objects, transfer data, and configure MCP, FUSE, IAM, security, lifecycle… | https://cloud.google.com/storage |
| `hostinger` | Deploy, manage and monitor your Hostinger services directly from Claude Code. The plugin connects Claude to Hostinger's remote MCP… | https://www.hostinger.com |
| `railway` | Deploy and manage apps, databases, and infrastructure on Railway. Covers project setup, deploys, environment configuration, networking,… | https://docs.railway.com/ai/claude-code-plugin |
| `render` | Deploy, debug, and monitor applications on Render. Includes skills, an agent, slash commands, and a render.yaml validation hook. | https://render.com |
| `valtown` | Build and deploy on Val Town. Bundles the Val Town MCP server and platform skills (HTTP vals, cron/intervals, SQLite, email, OAuth,… | https://val.town |
| `vercel` | Vercel deployment platform integration. Manage deployments, check build status, access logs, configure domains, and control your… | https://github.com/vercel/vercel-plugin |

### Monitoring (22)

| Plugin | What it does | Help page |
|---|---|---|
| `amplitude` | Use Amplitude as an expert analyst — instrument Amplitude, discover product opportunities, analyze charts, create dashboards, manage… | https://github.com/amplitude/mcp-marketplace |
| `dash0` | OpenTelemetry observability for Claude Code sessions. Captures tool calls, LLM invocations, token usage, and errors as OTel traces. Send… | https://dash0.com/ |
| `datadog` | Use Datadog directly in Claude Code through a preconfigured Datadog MCP server. Query logs, metrics, traces, dashboards, and more… | https://www.datadoghq.com/ |
| `dynatrace` | Dynatrace observability skills: DQL query patterns, application and infrastructure monitoring, log analysis, problem investigation, and… | https://www.dynatrace.com/hub/detail/claude-code-cli/ |
| `fullstory` | Connect Claude to Fullstory to query behavioral analytics, session replays, and customer experience insights. | https://www.fullstory.com |
| `grafana-assistant` | Skills and rules for developing and using the Grafana Assistant app and CLI. | https://grafana.com |
| `grafana-cloud-mcp` | Hosted MCP server for AI-assisted Grafana Cloud observability — no local installation required. | https://grafana.com |
| `grafana-mcp` | MCP server for AI-assisted Grafana dashboard, datasource, alerting, and incident management. | https://grafana.com |
| `honeycomb` | Skills, agents, and workflows for Honeycomb observability — query patterns, production investigations, SLOs, OpenTelemetry… | https://www.honeycomb.io |
| `incident-io` | Work with incident.io from Claude: respond to and investigate incidents, check on-call schedules and escalations, and author the… | https://incident.io |
| `langfuse` | Skills for working with Langfuse, the open-source LLM engineering platform for tracing, prompt management, and evaluation. | https://langfuse.com |
| `langfuse-observability` | Langfuse observability plugin for Claude Code — captures and exports traces, spans, and session telemetry from Claude Code to Langfuse… | https://langfuse.com/integrations/other/claude-code |
| `logfire` | Add Logfire observability to Python applications with auto-instrumentation for FastAPI, httpx, asyncpg, SQLAlchemy, and more | https://github.com/pydantic/skills/tree/main/plugins/logfire |
| `logrocket` | Connect Claude Code to LogRocket to query session replays, metrics, issues, and user behavior using natural language. | https://logrocket.com |
| `mlflow` | Skills for tracing, evaluating, and improving AI agents with MLflow. Supports the full agent improvement loop: instrument → trace →… | https://mlflow.org/ |
| `newrelic` | New Relic observability intelligence for Claude Code. Investigate APM performance, analyze cloud costs, debug Kubernetes, write NRQL… | https://newrelic.com |
| `noibu` | Built for ecommerce, the Noibu plugin bridges the gap between customer experience and revenue by connecting Claude directly to your… | https://help.noibu.com/articles/3918362002-overview-of-the-noibu-plugin-for-claude |
| `pagerduty` | Enhance code quality and security through PagerDuty risk scoring and incident correlation. Score pre-commit diffs against historical… | https://github.com/PagerDuty/claude-code-plugins |
| `posthog` | Access PostHog analytics, feature flags, experiments, error tracking, and insights directly from Claude Code. | https://posthog.com/docs/model-context-protocol |
| `rootly` | Full-lifecycle incident management: deploy safety, incident response, on-call management, and retrospectives. | https://rootly.com |
| `sentry` | Sentry error monitoring integration. Access error reports, analyze stack traces, search issues by fingerprint, and debug production… | https://github.com/getsentry/plugin-claude |
| `sentry-cli` | Skills for using the Sentry CLI to interact with Sentry from the command line | https://sentry.io |

### Security (18)

| Plugin | What it does | Help page |
|---|---|---|
| `42crunch-api-security-testing` | Automate API security directly in Claude Code with 42Crunch - automatically audit OpenAPI specs, detect vulnerabilities aligned with… | https://42crunch.com |
| `auth0` | Enterprise-grade auth, easy to implement. Add login, SSO, MFA, and access control to any app with framework-aware guidance. | https://auth0.com |
| `claude-security` | Deep vulnerability scanning of your own code, run entirely inside your Claude Code session at a chosen effort tier, with every finding… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-security |
| `crowdsec` | Operational skill for installing, configuring, operating, and debugging CrowdSec (cscli, LAPI/CAPI, hub, bouncers, WAF/AppSec) across… | https://www.crowdsec.net |
| `crowdstrike-falcon-foundry` | CrowdStrike Falcon Foundry development skills for building cybersecurity applications on the Falcon platform. Includes UI development,… | https://github.com/CrowdStrike/foundry-skills |
| `crowdstrike-falcon-fusion` | CrowdStrike Falcon Fusion skills for authoring, deploying, and executing Fusion workflows. Includes live action discovery, YAML… | https://github.com/CrowdStrike/fusion-skills |
| `duende-skills` | Duende development skills and agents for Claude Code — covering OAuth/OIDC protocols, IdentityServer, token management, ASP.NET Core… | https://duendesoftware.com |
| `jfrog` | Use the JFrog Platform from Claude Code: Artifactory repos and artifacts, security findings and exposures, Catalog package safety and… | https://jfrog.com |
| `security-guidance` | Security review for Claude-generated code. Pattern-based warnings on edits, LLM-powered diff review on Stop, and an agentic commit… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/security-guidance |
| `semgrep` | Semgrep catches security vulnerabilities in real-time and guides Claude to write secure code from the start. | https://github.com/semgrep/mcp-marketplace |
| `sonarqube` | Automatically enforce SonarQube code quality and security in the agent coding loop — 7,000+ rules, secrets scanning, agentic analysis,… | https://www.sonarsource.com |
| `sonatype-guide` | Sonatype Guide MCP server for software supply chain intelligence and dependency security. Analyze dependencies for vulnerabilities, get… | https://github.com/sonatype/sonatype-guide-claude-plugin |
| `stackhawk-api` | Query the StackHawk platform API for security posture reporting, findings analysis, and app management. Guides agents through… | https://docs.stackhawk.com/ai-security/ |
| `stackhawk-hawkscan` | Configure, run, and interpret HawkScan DAST results inside Claude Code. Generates stackhawk.yml configs, runs scans via CLI or Docker,… | https://docs.stackhawk.com/ai-security/ |
| `vanta` | The Vanta plugin connects Claude Code to Vanta's security and compliance platform through the Vanta MCP server. It combines Vanta's… | https://help.vanta.com/en/articles/14094979-connecting-to-vanta-mcp#h_887ce3f337 |
| `vanta-mcp-plugin` | The Vanta plugin connects Claude Code to Vanta's security and compliance platform through the Vanta MCP server. It combines Vanta's… | https://help.vanta.com/en/articles/14094979-connecting-to-vanta-mcp#h_887ce3f337 |
| `workos` | WorkOS integration skills for AuthKit, SSO, Directory Sync, RBAC, Vault, Audit Logs, migrations, and API references. | https://workos.com |
| `zscaler` | Manage Zscaler cloud security platform including ZPA (private access), ZIA (internet access), ZDX (digital experience), ZCC (client… | https://github.com/zscaler/zscaler-mcp-server |

### Testing (2)

| Plugin | What it does | Help page |
|---|---|---|
| `growthbook` | A suite of agent skills for the full GrowthBook feature flag and experimentation lifecycle. | https://growthbook.io |
| `playwright` | Browser automation and end-to-end testing MCP server by Microsoft. Enables Claude to interact with web pages, take screenshots, fill… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/playwright |

### Design (8)

| Plugin | What it does | Help page |
|---|---|---|
| `adobe-for-creativity` | Harness Adobe's creative AI-powered tools to edit images, automate design workflows, and bring creative visions to life — from… | https://github.com/adobe/skills/tree/main/plugins/creative-cloud/adobe-for-creativity |
| `canva` | Create, edit, review, resize, and brand-check Canva designs with the Canva MCP server. | https://www.canva.com |
| `figma` | Figma design platform integration. Access design files, extract component information, read design tokens, and translate designs into… | https://github.com/figma/mcp-server-guide |
| `hyperframes` | HyperFrames by HeyGen. Write HTML, render video. Compositions, GSAP and runtime adapter animations, captions, voiceovers, audio-reactive… | https://hyperframes.heygen.com |
| `miro` | Secure access to Miro boards. Enables AI to read board context, create diagrams, and generate code with enterprise-grade security. | https://miro.com |
| `runway-api` | Video generation at scale. Generate videos, images, and audio with Runway's API — batch ad campaigns, product videos, multishot stories,… | https://runwayml.com |
| `superdesign` | Design or redesign frontend UI and marketing graphics on the Superdesign infinite canvas. Reads your codebase for context, sets up a… | https://superdesign.dev |
| `ui-theme-designer` | Plugin for coding agents working with UI theme designer. Bundles two skills: how-to and conceptual answers about UI theme designer on… | https://github.com/SAP/ui-theme-designer-plugins-for-coding-agents |

### Productivity (69)

| Plugin | What it does | Help page |
|---|---|---|
| `activecampaign` | Marketing automation, CRM, and email marketing powered by ActiveCampaign. Manage contacts, campaigns, automations, deals, and get… | https://www.activecampaign.com |
| `airtable` | Airtable is the database and operations layer for your agents — whether running product, marketing, sales, ops, HR, or a custom business… | https://www.airtable.com |
| `airwallex-agentos` | Bring Airwallex's global financial infrastructure to Claude. Orchestrate actions across your account in plain language, e.g., set up… | https://www.airwallex.com/docs |
| `amazon-selling-partner` | Connect your Amazon Seller Central account to Claude. Ask about sales, inventory, and listing performance and get recommendations… | https://github.com/amzn/selling-partner-agentic-toolkit |
| `apollo` | Prospect, enrich leads, load outreach sequences, and query sales analytics with Apollo.io — one-click MCP server integration for Claude… | https://www.apollo.io/ |
| `asana` | Asana project management integration. Connects Claude Code to Asana's V2 MCP server to create and manage tasks, search projects, update… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/asana |
| `atlassian` | Connect to Atlassian products including Jira and Confluence. Search and create issues, access documentation, manage sprints, and… | https://github.com/atlassian/atlassian-mcp-server |
| `atlassian-twg-cli` | Teamwork Graph CLI is Atlassian's agent-first interface to your entire work context: Jira issues, Confluence pages, Bitbucket PRs, along… | https://developer.atlassian.com/cloud/twg-cli/ |
| `blackrock-advisor-center-plugin` | BlackRock Advisor Center 360° skills for financial advisors: portfolio review, opportunity and fund-health checks, guided benchmark… | https://github.com/blackrock/advisor-center-agent-skills |
| `box` | Work with your Box content directly from Claude Code — search files, organize folders, collaborate with your team, and use Box AI to… | https://github.com/box/skills |
| `carbone-skill` | Official Carbone skill — complete templating language reference covering tags, loops, conditions, formatters, aggregators, and all… | https://carbone.io |
| `carta-cap-table` | Carta Cap Table plugin — skills and hooks for querying cap tables, grants, SAFEs, 409A valuations, waterfall scenarios, and more | https://carta.com |
| `carta-crm` | Manage the Carta CRM conversationally — search, add, update, and enrich investors, companies, contacts, deals, notes, and fundraisings… | https://carta.com |
| `carta-investors` | Carta Investors plugin — skills for querying investor data, performance benchmarks, regulatory reporting, AGM deck generation, brand… | https://carta.com |
| `chronograph-gp` | Portfolio monitoring, valuations and analytics for private-capital GP teams using the Chronograph connector: portfolio-company… | https://www.chronograph.pe/ |
| `chronograph-lp` | Portfolio monitoring and analytics for private-capital LP teams using the Chronograph connector: cashflow forecasting, commitment… | https://www.chronograph.pe/ |
| `circleback` | Circleback conversational context integration. Search and access meetings, emails, calendar events, and more. | https://github.com/circlebackai/claude-code-plugin |
| `claude-code-setup` | Analyze codebases and recommend tailored Claude Code automations such as hooks, skills, MCP servers, and subagents. | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-code-setup |
| `claude-md-management` | Tools to maintain and improve CLAUDE.md files - audit quality, capture session learnings, and keep project memory current. | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-md-management |
| `clay` | Work with Clay from Claude Code: set up and sign in to the clay CLI, query and analyze Clay tables, search Clay's GTM database for… | https://github.com/clay-run/agent-plugins/tree/main/clay |
| `code-review` | Automated code review for pull requests using multiple specialized agents with confidence-based scoring to filter false positives | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/code-review |
| `code-simplifier` | Agent that simplifies and refines code for clarity, consistency, and maintainability while preserving functionality. Focuses on recently… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/code-simplifier |
| `coderabbit` | Your code review partner. CodeRabbit provides external validation using a specialized AI architecture and 40+ integrated static… | https://github.com/coderabbitai/skills |
| `commit-commands` | Commands for git commit workflows including commit, push, and PR creation | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/commit-commands |
| `cwc-makers` | Onboard a Code-with-Claude Makers Cardputer with one /maker-setup command — clones the build-with-claude repo, flashes UIFlow firmware,… | https://claude.com/cwc-makers |
| `desktop-commander` | MCP server for terminal commands, process management, and file operations across text, code, PDF, DOCX, Excel, images, and structured data. | https://desktopcommander.app |
| `discord` | Discord messaging bridge with built-in access control. Manage pairing, allowlists, and policy via /discord:access. | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/discord |
| `dropbox` | The Dropbox plugin for Claude connects your Dropbox files directly to Claude, so you can search, organize, save generated content, and… | https://www.dropbox.com |
| `exa` | Exa AI web search, deep research, and content extraction. Provides MCP tools and research skills for comprehensive web search, people… | https://exa.ai/docs/reference/exa-mcp |
| `gc-ai` | Work in your GC AI legal knowledge base from Claude: upload documents, run review playbooks, and ask questions grounded in your own… | https://docs.gc.ai/api-reference/mcp/overview |
| `github` | Official GitHub MCP server for repository management. Create issues, manage pull requests, review code, search repositories, and… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/github |
| `gitlab` | GitLab DevOps platform integration. Manage repositories, merge requests, CI/CD pipelines, issues, and wikis. Full access to GitLab's… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/gitlab |
| `govtribe` | Government contracting research and capture workflows in Claude: opportunity and pipeline briefs, bid/no-bid and competitor analysis,… | https://govtribe.com |
| `hookify` | Easily create custom hooks to prevent unwanted behaviors by analyzing conversation patterns or from explicit instructions. Define rules… | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/hookify |
| `hubspot-sales` | Run your HubSpot sales workflow directly from Claude. Adds skills that cover the full sales day: import contacts and deals into HubSpot,… | https://www.hubspot.com |
| `hunter` | Find and verify professional email addresses, search contacts by domain, and enrich company data -- directly in Claude. | https://hunter.io |
| `imessage` | iMessage messaging bridge with built-in access control. Reads chat.db directly, sends via AppleScript. Manage pairing, allowlists, and… | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/imessage |
| `intercom` | Intercom integration for Claude Code. Search conversations, analyze customer support patterns, look up contacts and companies, and… | https://github.com/intercom/claude-plugin-external |
| `intuit-quickbooks` | QuickBooks business insights and actions: financial health briefings across P&L, cash flow, balance sheet and A/R, industry… | https://github.com/intuit/quickbooks-claude-plugin |
| `leadfeeder` | Turn website visitor signals into pipeline with Leadfeeder: daily visitor briefs, visitor company research, buyer and contact discovery,… | https://www.leadfeeder.com |
| `legalzoom` | Attorney guidance and legal tools for business and personal needs. AI-powered document review identifies critical risks and important… | https://www.legalzoom.com/ |
| `linear` | Linear issue tracking integration. Create issues, manage projects, update statuses, search across workspaces, and streamline your… | https://github.com/anthropics/claude-plugins-public/tree/main/external_plugins/linear |
| `linq-alpha` | LinqAlpha financial research in Claude: guided setup for the LinqAlpha connector, capability-based source selection for fundamentals,… | https://www.linqalpha.com |
| `lusha` | Prospect, enrich, and build call-ready lead lists using Lusha's B2B intelligence platform — verified phone numbers, company signals, and… | https://www.lusha.com |
| `monday-crm` | Run your monday CRM in plain language. Build a pipeline from scratch, start the day with a ranked deal briefing, spin up a forecast… | https://monday.com |
| `netsuite-ai-companion` | Guides AI assistants that use the NetSuite AI Connector: tool-selection order, output formatting, NetSuite domain knowledge,… | https://github.com/oracle/netsuite-suitecloud-sdk/tree/ai-plugins-dist/anthropic/netsuite-ai-companion |
| `netsuite-finance-analyst` | Director-level finance analysis on live NetSuite data: financial reporting, period close, variance, aging and reconciliation reviews,… | https://github.com/oracle/netsuite-suitecloud-sdk/tree/ai-plugins-dist/anthropic/netsuite-finance-analyst |
| `notion` | Notion workspace integration. Search pages, create and update documents, manage databases, and access your team's knowledge base… | https://github.com/makenotion/claude-code-notion-plugin |
| `pendo-analytics` | Bring Pendo product analytics into Claude Code: account health, feature adoption, session replay lookup and triage, feedback analysis,… | https://github.com/pendo-io/claude-pendo-plugin/tree/main/plugins/pendo-analytics |
| `pendo-guides` | Create production-ready Pendo in-app guides (walkthroughs, announcements, alerts, polls, promotions) as HTML/CSS/JS from a short intake… | https://github.com/pendo-io/claude-pendo-plugin/tree/main/plugins/pendo-guides |
| `pendo-orchestrate` | Create, configure and edit draft Pendo Orchestrate email journeys, including multi-email and conditional split flows, via the Pendo… | https://github.com/pendo-io/claude-pendo-plugin/tree/main/plugins/pendo-orchestrate |
| `pigment` | Analyze business data and build custom Pigment models, metrics, and boards through natural language. | https://www.pigment.com |
| `pr-review-toolkit` | Comprehensive PR review agents specializing in comments, tests, error handling, type design, code quality, and code simplification | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/pr-review-toolkit |
| `project-artifact` | Generate and publish a living project status page — overview & success criteria, the workstream sequence, and next steps — as a… | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/project-artifact |
| `receipts` | A personal Claude Code impact report for justifying your usage to a manager or a self-review: what you shipped, which projects it went… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/receipts |
| `save-to-spotify` | Create polished audio episodes with TTS narration, rich timelines, cover images, and save them to Spotify via the save-to-spotify CLI. | https://github.com/spotify/save-to-spotify |
| `session-report` | Generate an explorable HTML report of Claude Code session usage — tokens, cache efficiency, subagents, skills, and the most expensive… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/session-report |
| `shippo` | Shippo connects you to USPS, UPS, FedEx, DHL, and 40+ carriers, so you can handle a shipment end to end right inside Claude. Compare… | https://docs.goshippo.com |
| `slack` | Slack workspace integration. Search messages, access channels, read threads, and stay connected with your team's communications while… | https://github.com/slackapi/slack-mcp-plugin/tree/main |
| `spotify-ads-api` | Manage Spotify ad campaigns with natural language. Create campaigns, ad sets, ads, pull reports, and handle OAuth — all through… | https://github.com/spotify/ads-claude-plugin |
| `telegram` | Telegram messaging bridge with built-in access control. Manage pairing, allowlists, and policy via /telegram:access. | https://github.com/anthropics/claude-plugins-official/tree/main/external_plugins/telegram |
| `vanguard-advisor-tools` | Vanguard Advisor Tools for financial professionals: research and compare funds and ETFs across the industry and prepare for client… | https://advisors.vanguard.com |
| `vibe-prospecting` | Vibe Prospecting connects Claude to live B2B company and contact data so users can search, match, enrich, filter, and export prospects… | https://www.vibeprospecting.ai/product/claude-plugin |
| `windsor-ai` | Connect Claude Code to 325+ business data sources via Windsor.ai. Query marketing, sales, CRM, ecommerce, finance, and analytics data… | https://windsor.ai |
| `wingspan` | Ask Claude about the contractors you pay through Wingspan, what you owe them, and what is holding up a payment, then onboard contractors… | https://github.com/wingspanHQ/mcp-claude-plugin |
| `youdotcom-agent-skills` | You.com agent skills for web search, research with citations, and content extraction. Guided integrations for Vercel AI SDK, Claude… | https://you.com |
| `zapier` | Connect 8,000+ apps to your AI workflow. Discover, enable, and execute Zapier actions directly from your client. | https://github.com/zapier/zapier-mcp/tree/main/plugins/zapier |
| `zocks-advisor` | Seven skills for financial advisors built on Zocks meeting intelligence: client behavioral profiles, attrition-risk ranking, held-away… | https://github.com/zocks-communications/zocks-agent-plugins |
| `zoominfo` | Search companies and contacts, enrich leads, find lookalikes, and get AI-ranked contact recommendations. Pre-built skills chain multiple… | https://www.zoominfo.com |

### Automation (3)

| Plugin | What it does | Help page |
|---|---|---|
| `browser-use` | Give Claude a real browser — your Chrome or a Browser Use Cloud browser. Use it whenever a task involves a website or web app: browsing,… | https://browser-use.com |
| `synthflow` | Connects Claude Code to the Synthflow AI voice-agent platform through its hosted MCP server, with skills for reviewing calls and… | https://synthflow.ai |
| `zyte-web-data` | Web scraping skills for Claude Code powered by the Zyte API — scrape sites, generate and run Scrapy spiders, define extraction schemas,… | https://www.zyte.com |

### Migration (1)

| Plugin | What it does | Help page |
|---|---|---|
| `aws-transform` | Migrate, modernize, and upgrade codebases to AWS. Transforms .NET Framework to .NET 8/10, mainframe COBOL to Java, VMware VMs to EC2,… | https://github.com/awslabs/agent-plugins |

### Learning (3)

| Plugin | What it does | Help page |
|---|---|---|
| `explanatory-output-style` | Adds educational insights about implementation choices and codebase patterns (mimics the deprecated Explanatory output style) | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/explanatory-output-style |
| `learn-with-coursera` | Turn any learning intent into a personalized Coursera experience. Asks three quick questions (topic, familiarity, preferred format),… | https://github.com/coursera/skills |
| `learning-output-style` | Interactive learning mode that requests meaningful code contributions at decision points (mimics the unshipped Learning output style) | https://github.com/anthropics/claude-plugins-public/tree/main/plugins/learning-output-style |

### Location (2)

| Plugin | What it does | Help page |
|---|---|---|
| `amazon-location-service` | Guide developers through adding maps, places search, geocoding, routing, and other geospatial features with Amazon Location Service,… | https://github.com/awslabs/agent-plugins |
| `mapbox` | Mapbox skills and MCP servers for building location-aware applications with AI. Includes geospatial tools, style management, and… | https://www.mapbox.com |

### Math (2)

| Plugin | What it does | Help page |
|---|---|---|
| `math-olympiad` | Solve competition math (IMO, Putnam, USAMO) with adversarial verification that catches what self-verification misses. Fresh-context… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/math-olympiad |
| `math-proof` | Two skills for hard mathematics problems, each ending in a self-contained proof.md: /math-proof:solo has the session work the problem… | https://github.com/anthropics/claude-plugins-official/tree/main/plugins/math-proof |

### Other (14)

| Plugin | What it does | Help page |
|---|---|---|
| `ai-plugins` | Set up endorctl and use Endor Labs to scan, prioritize, and fix security risks across your software supply chain | https://www.endorlabs.com |
| `aikido` | Aikido Security scanning for Claude Code — SAST, secrets, and IaC vulnerability detection powered by the Aikido MCP server. | https://github.com/AikidoSec/aikido-claude-plugin |
| `atlan` | Atlan data catalog plugin for Claude Code. Search, explore, govern, and manage your data assets through natural language. Powered by the… | https://docs.atlan.com/ |
| `brightdata-plugin` | Web scraping, Google search, structured data extraction, and MCP server integration powered by Bright Data. Includes 7 skills: scrape… | https://docs.brightdata.com |
| `build-with-wordpress` | Craft production-grade WordPress sites and applications. Everything from themes and plugins to commerce and deployment. | https://developer.wordpress.com/wordpress-com-claude-code-plugin/ |
| `cloudinary` | Use Cloudinary directly in Claude. Manage assets, apply transformations, optimize media, and more through natural conversation. | https://cloudinary.com/documentation |
| `data-engineering` | Data engineering plugin - warehouse exploration, pipeline authoring, Airflow integration | https://github.com/astronomer/agents |
| `fastly-agent-toolkit` | Fastly development tools and platform skills | https://github.com/fastly/fastly-agent-toolkit/blob/main/README.md |
| `fiftyone` | Build high-quality datasets and computer vision models. Visualize datasets, analyze models, find duplicates, run inference, evaluate… | https://docs.voxel51.com/ |
| `nightvision` | Skills for working with NightVision, a DAST and API Discovery platform that finds exploitable vulnerabilities in web applications and… | https://github.com/nvsecurity/nightvision-skills |
| `nimble` | Nimble web data toolkit — search, extract, map, crawl the web and work with structured data agents | https://docs.nimbleway.com/integrations/agent-skills/plugin-installation |
| `postiz` | Social media automation CLI for scheduling posts, managing integrations, uploading media, and tracking analytics across 28+ platforms… | https://postiz.com/agent |
| `prisma` | Prisma MCP integration for Postgres database management, schema migrations, SQL queries, and connection string management. Provision… | https://prisma.io |
| `remember` | Continuous memory for Claude Code. Extracts, summarizes, and compresses conversations into tiered daily logs. Claude remembers what you… | https://github.com/Digital-Process-Tools/claude-remember |

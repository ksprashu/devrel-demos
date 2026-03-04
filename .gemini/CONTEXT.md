# 🌐 PROJECT CONTEXT

## 🛠 TECH STACK
- **Monorepo:** Google Cloud DevRel Demos
- **Languages:** Python, Go, Java, JavaScript/TypeScript (Next.js)
- **AI Frameworks:** Agent Development Kit (ADK), Google Gen AI SDK (`@google/genai`, `google-genai`), Genkit
- **Cloud Infrastructure:** Google Cloud (Vertex AI, Cloud Run, GKE, BigQuery, Dataplex, AlloyDB, etc.)
- **Provisioning:** Terraform
- **CI/CD:** GitHub Actions, Google Cloud Build
- **Testing:** Python `unittest`, Go `testing`, Java JUnit

## 📜 STANDARDS & CONVENTIONS
- **Precedence:** Sub-project `GEMINI.md` files take absolute precedence over global defaults.
- **Python:** Use `uv`, FastAPI, Google Style guides. Projects like `AIDA` use `ruff`.
- **Go:** `gofmt` required, `camelCase` (unexported) / `PascalCase` (exported), explicit error handling.
- **AI/ML:** Prefer Gemini 2.5/3.0 models. TDD for agents.
- **Source Control:** Do not stage/commit unless asked. Follow PR template logic.
- **Automation:** Use `Makefile` where available.

## 🔗 KEY LINKS
- **Repo:** github.com/GoogleCloudPlatform/devrel-demos
- **Contributing:** .github/CONTRIBUTING.md

# Solvapay Skills

Agent skills for integrating Solvapay SDK and onboarding providers.

## Available Skills

| Skill | Purpose |
| --- | --- |
| [solvapay](solvapay/) | Router skill that dispatches to the right specialist skill |
| [integrate-solvapay-sdk](integrate-solvapay-sdk/) | Implement Solvapay SDK flows in Next.js, React, Express, and MCP server stacks |
| [onboard-solvapay-provider](onboard-solvapay-provider/) | Onboard provider account, products/plans, sandbox testing, and go-live |
| [integrate-website-checkout](integrate-website-checkout/) | Add hosted Solvapay checkout and customer portal to website apps |

## Which Skill Should I Use?

- "Protect my Express API with paywall checks" -> `integrate-solvapay-sdk` (`express` path)
- "Set up provider account and launch billing" -> `onboard-solvapay-provider`
- "Add hosted checkout to my Next.js site" -> `integrate-website-checkout`
- "Not sure where to start" -> `solvapay` router skill

## Documentation Source Priority

All skills use the same retrieval chain:

1. SolvaPay Docs MCP server: https://docs.solvapay.com/mcp
2. Fallback docs index: https://docs.solvapay.com/llms.txt
3. Direct docs.solvapay.com page fetch

If MCP is unavailable, skills continue with fallbacks. MCP setup is a recommended optional improvement.

## Installation

Install specific skills (recommended) using the `skills` CLI:

```bash
npx skills add https://github.com/solvapay/solvapay-skills --skill solvapay --skill integrate-solvapay-sdk --skill onboard-solvapay-provider --skill integrate-website-checkout
```

Install only one skill:

```bash
npx skills add https://github.com/solvapay/solvapay-skills --skill integrate-solvapay-sdk
```

Install all available skills:

```bash
npx skills add https://github.com/solvapay/solvapay-skills --all
```

## Local Development and Testing Workflow

1. Edit a skill file in this repository.
2. Install/update locally with `npx skills add <repo-or-path> --skill <skill-name>`.
3. Run 2-3 prompt checks:
   - routing intent prompt
   - happy-path implementation prompt
   - failure-path/troubleshooting prompt
4. Verify outputs follow skill guardrails and docs source priority.

## Skill Quality Expectations

A skill is considered complete when:

- it has clear when-to-use scope
- it has guardrails with explicit "Never" and "Always" rules
- it has step-by-step implementation flow
- it has verification and troubleshooting guidance
- it uses docs-only, topic-based references resilient to docs URL changes

## Architecture

- `solvapay/` routes requests by intent.
- `integrate-solvapay-sdk/` is the primary implementation skill.
- `onboard-solvapay-provider/` handles operational provider setup.
- `integrate-website-checkout/` is the focused hosted checkout website path.

# Awesome AI Design Workflows [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Tools, standards, patterns, and research for teams putting AI into real design work.

This list is for product design teams and the engineers who work with them: what to use when an agent is part of the design process, what standards to build against, and what the research actually shows. Every entry is a link we checked and something we would hand a colleague. Anything that is marketing with no substance behind it is left out, including our own.

## Contents

- [Standards and specs](#standards-and-specs)
- [Agent skills for design work](#agent-skills-for-design-work)
- [MCP servers worth wiring up](#mcp-servers-worth-wiring-up)
- [Design to code](#design-to-code)
- [Generating UI and mockups](#generating-ui-and-mockups)
- [Design systems and tokens](#design-systems-and-tokens)
- [Research and synthesis](#research-and-synthesis)
- [Accessibility checks an agent can run](#accessibility-checks-an-agent-can-run)
- [Visual and behavioral QA](#visual-and-behavioral-qa)
- [Patterns for designing AI products](#patterns-for-designing-ai-products)
- [Papers and datasets](#papers-and-datasets)
- [Reading](#reading)
- [Related lists](#related-lists)
- [Who maintains this](#who-maintains-this)

## Standards and specs

Build against these and your workflow survives a model change.

- [Agent Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) - How a folder holding a `SKILL.md` file becomes a capability an agent loads only when it is relevant.
- [Model Context Protocol](https://modelcontextprotocol.io/) - The open protocol agents use to reach tools and data, and how design tools expose themselves to a model.
- [AGENTS.md](https://agents.md/) - Convention for the instruction file coding agents read in a repository.
- [Design Tokens Format Module](https://www.designtokens.org/tr/drafts/format/) - The community-group draft spec for exchanging design tokens as JSON, the format worth generating into.
- [WCAG 2.2](https://www.w3.org/TR/WCAG22/) - The accessibility success criteria a design review should cite by number instead of by opinion.
- [ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/) - Reference keyboard behavior and structure per component pattern, useful as ground truth when a model asserts otherwise.
- [Open UI](https://open-ui.org/) - Community work naming component anatomy and states, which gives cross-team vocabulary a model can be held to.
- [llms.txt](https://llmstxt.org/) - Proposal for a plain-text file describing what a site contains, for the case where the reader is a model.

## Agent skills for design work

- [anthropics/skills](https://github.com/anthropics/skills) - Anthropic's own skills, including document and slide generation, and the clearest reference for how a skill is structured.
- [Claude Code best practices](https://code.claude.com/docs/en/best-practices) - How to shape instructions, context, and tools for agentic work in a repository.
- [claude-cookbooks](https://github.com/anthropics/claude-cookbooks) - Runnable notebooks for tool use, vision, and evaluation, including the vision recipes that matter for screenshot work.
- [anthropics/claude-code](https://github.com/anthropics/claude-code) - Issue tracker and docs for the terminal agent most of these skills run inside.

Maintained by us, the maintainers of this list, and MIT licensed:

- [design-review](https://github.com/humbleteam/design-review) - Structured UX critique with a 0-4 score, Before/After/Why fixes, and a citation per claim.
- [ascii-wireframes](https://github.com/humbleteam/ascii-wireframes) - Three distinct layout hypotheses as ASCII wireframes before any hi-fi work starts.
- [html-mockup](https://github.com/humbleteam/html-mockup) - Census-first HTML mockups that match a reference screenshot on palette, item counts, and states.
- [extract-design-tokens](https://github.com/humbleteam/extract-design-tokens) - Palette, type, spacing, radii, and shadows pulled from a URL or screenshot into CSS variables and JSON.
- [audit-design-tokens](https://github.com/humbleteam/audit-design-tokens) - Token drift report for a codebase: raw hex values, off-scale spacing, near-duplicate colors.
- [design-qa](https://github.com/humbleteam/design-qa) - Pre-ship gate over states, contrast, touch targets, breakpoints, and keyboard paths.
- [design-handoff](https://github.com/humbleteam/design-handoff) - A finished mockup turned into a dev-ready spec with tokens, states, a11y annotations, and open questions.
- [accessibility-audit](https://github.com/humbleteam/accessibility-audit) - WCAG 2.2 review with success-criterion citations and P0-P2 severity.
- [ux-writing](https://github.com/humbleteam/ux-writing) - Interface copy rules plus a pass that strips the tells of generated text.
- [design-brief](https://github.com/humbleteam/design-brief) - Messy inputs turned into a 5-bullet brief with a gap report for what the input never answered.

## MCP servers worth wiring up

- [Figma MCP server](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Figma-MCP-server) - Figma's own server, so an agent reads the selected frame's structure, variables, and generated code instead of guessing from an image.
- [chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp) - Chrome DevTools exposed to an agent: load a page, inspect the rendered layout, record a performance trace.
- [playwright-mcp](https://github.com/microsoft/playwright-mcp) - Browser control over MCP driven by the accessibility tree rather than screenshots, which also makes it a keyboard-path checker.
- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) - The reference server collection, useful for seeing how a tool surface should be described to a model.

## Design to code

- [Claude Code](https://claude.com/product/claude-code) - Terminal agent that edits a real repository, which is where design-to-code work ends up living.
- [Cursor](https://cursor.com/) - Editor built around model-assisted edits across a whole codebase.
- [v0](https://v0.app/) - Prompt to React and Tailwind UI, strongest as a starting point rather than a finish line.
- [Lovable](https://lovable.dev/) - Prompt to a deployed full-stack app, aimed at non-engineers who need something running.
- [Bolt](https://bolt.new/) - In-browser prompt-to-app with the dev environment and preview attached.
- [Onlook](https://github.com/onlook-dev/onlook) - Open-source visual editor that writes changes back into React source.
- [Visual Copilot](https://www.builder.io/blog/figma-to-code-visual-copilot) - Figma frame to component code, with mapping onto your own components.
- [Locofy](https://www.locofy.ai/) - Figma to front-end code with tagging of layers into components and states.
- [Anima](https://www.animaapp.com/) - Design file to React, Vue, or HTML, plus a code-back-to-design direction.
- [UXPin Merge](https://www.uxpin.com/merge) - Prototyping directly on your coded components, so a prototype cannot drift from what is shipped.
- [html.to.design](https://www.figma.com/community/plugin/1159123024924461424/html-to-design-by-divriots-import-websites-to-figma-designs-web-html-css) - Any live URL imported back into editable Figma layers, the fastest way to get a real page into a design file.

## Generating UI and mockups

- [Stitch](https://stitch.withgoogle.com/) - Google's tool for generating mobile and web UI from a prompt or an image, for ideation speed.
- [BuildMuse](https://buildmuse.design/) - Curated UI, app, web, icon, and motion references with an AI chat for turning rough ideas into concise design directions.
- [Figma Make](https://www.figma.com/blog/introducing-figma-make/) - Figma's prompt-to-working-prototype feature, announced in this post.
- [Magic Patterns](https://www.magicpatterns.com/) - Prompt to UI that can be pointed at your own design system rather than a generic kit.
- [Subframe](https://www.subframe.com/) - Design tool built around real components that outputs React and Tailwind.
- [Motiff](https://www.motiff.com/) - Design editor with AI generation and a system-consistency check over what it produces.
- [Uizard](https://uizard.io/) - Low-effort wireframing and screen generation, useful for early rounds with non-designers.
- [Visily](https://www.visily.ai/) - Wireframes and prototypes from screenshots, sketches, or text, aimed at mixed teams.
- [Framer](https://www.framer.com/) - Site builder with generation features where the output is a publishable site.
- [Relume](https://www.relume.ai/) - Section library and generator for Webflow-shaped marketing pages.
- [Penpot](https://penpot.app/) - Open-source design tool with an open file format and plugin API, which is what makes it scriptable by an agent.

## Design systems and tokens

- [Tokens Studio](https://tokens.studio/) - Token management for Figma with sync to code, the usual bridge between a design file and a token pipeline.
- [tokens-studio/figma-plugin](https://github.com/tokens-studio/figma-plugin) - The plugin's source, worth reading if you generate token files programmatically.
- [Style Dictionary](https://styledictionary.com/) - Build system that turns one token source into platform-specific outputs.
- [Design Tokens Community Group](https://www.designtokens.org/) - The group behind the format spec, with the current state of the work.
- [Supernova](https://www.supernova.io/) - Design system documentation and code generation from design sources.
- [zeroheight](https://zeroheight.com/) - Documentation layer over an existing design system, where written guidance lives next to components.
- [The Component Gallery](https://component.gallery/) - Cross-system reference of how real design systems name and build each component.
- [Storybook](https://storybook.js.org/) - Component workbench, and the artifact worth pointing an agent at when it needs the true component states.

## Research and synthesis

- [Dovetail](https://dovetail.com/) - Research repository with AI-assisted tagging and summarizing over your own transcripts.
- [Marvin](https://heymarvin.com/) - Qualitative analysis tool that transcribes and clusters interview data.
- [Looppanel](https://www.looppanel.com/) - Notes, transcripts, and AI-assisted analysis for interview-heavy research.
- [Maze](https://maze.co/) - Unmoderated testing with automated analysis of task results.
- [Attention Insight](https://attentioninsight.com/) - Predicts where attention lands on a design from a model trained on eye-tracking data. Treat output as a hypothesis to test, not a finding.
- [Neurons](https://www.neuronsinc.com/) - Similar attention and engagement prediction, with the same caveat about treating predictions as evidence.

## Accessibility checks an agent can run

Every item here is scriptable, which means it can be a gate rather than a good intention.

- [axe-core](https://github.com/dequelabs/axe-core) - The accessibility rules engine most other tools wrap. Run it in CI.
- [axe DevTools](https://www.deque.com/axe/devtools/) - The browser-extension side of the same engine for manual passes.
- [pa11y](https://pa11y.org/) - Command-line accessibility testing.
- [pa11y-ci](https://github.com/pa11y/pa11y-ci) - The CI runner over a list of URLs, with per-page thresholds.
- [Accessibility Insights](https://accessibilityinsights.io/) - Microsoft's guided manual tests, which cover what automation cannot see.
- [Lighthouse](https://github.com/GoogleChrome/lighthouse) - Accessibility, performance, and best-practice audits in CI or DevTools.
- [Lighthouse accessibility scoring](https://developer.chrome.com/docs/lighthouse/accessibility/scoring) - What the score does and does not include, worth reading before quoting one.
- [WAVE](https://wave.webaim.org/) - Fast visual check of a single page's structure and errors.
- [eslint-plugin-jsx-a11y](https://github.com/jsx-eslint/eslint-plugin-jsx-a11y) - Catches a11y mistakes in JSX at lint time, before anything renders.
- [Storybook a11y addon](https://github.com/storybookjs/storybook/tree/next/code/addons/a11y) - Runs axe against every component story, so a failure lands on the component instead of the page.
- [WebAIM contrast checker](https://webaim.org/resources/contrastchecker/) - The reference contrast check for a specific pair of colors.
- [The A11Y Project](https://www.a11yproject.com/) - Practical checklists and short explainers to cite in reviews.
- [Inclusive Components](https://inclusive-components.design/) - Deep write-ups on building common components accessibly, one component per article.

## Visual and behavioral QA

- [Playwright](https://playwright.dev/) - Browser automation with screenshot comparison, the base layer for agent-driven UI checks.
- [Chromatic](https://www.chromatic.com/) - Visual regression review built on Storybook stories.
- [Percy](https://percy.io/) - Visual testing across browsers and widths as a CI gate.
- [Applitools](https://applitools.com/) - Visual testing with model-based comparison that tolerates rendering noise.

## Patterns for designing AI products

- [The Shape of AI](https://www.shapeof.ai/) - Pattern library for AI interfaces, organized by the job the pattern does.
- [AI UX Patterns](https://www.aiuxpatterns.com/) - Pattern exploration with a worked example showing how several patterns compose into one flow.
- [People + AI Guidebook](https://pair.withgoogle.com/guidebook/) - Google's chapters on mental models, explainability, feedback, and errors, with worksheets.
- [HAX Toolkit](https://www.microsoft.com/en-us/haxtoolkit/) - Microsoft's human-AI interaction guidelines plus a design library and a workbook per guideline.
- [IBM Design for AI](https://www.ibm.com/design/ai/) - Foundational principles and ethics-focused practices for AI products.
- [Apple HIG: machine learning](https://developer.apple.com/design/human-interface-guidelines/machine-learning) - Platform guidance on mistakes, corrections, and how much confidence to show a user.
- [NN/g on AI](https://www.nngroup.com/topic/ai/) - Nielsen Norman Group's research-backed articles on AI usability, and a useful counterweight to vendor claims.

## Papers and datasets

Read these before asserting what a model can do with a screen.

- [Design2Code](https://arxiv.org/abs/2403.03163) - Benchmark for turning a webpage screenshot into front-end code, with a hand-curated test set and human evaluation.
- [ScreenAI](https://arxiv.org/abs/2402.04615) - Vision-language model for UI and infographic understanding, including screen annotation and question answering.
- [Pix2Struct](https://arxiv.org/abs/2210.03347) - Screenshot parsing as pretraining, the idea behind treating a rendered UI as its own input modality.
- [Screen2Words](https://arxiv.org/abs/2108.03353) - Automatic summarization of a mobile screen's purpose, with the dataset behind it.
- [Sketch2Code](https://arxiv.org/abs/1905.13750) - Early work on generating a website from a paper mockup, useful for how the problem was framed.
- [WebArena](https://arxiv.org/abs/2307.13854) - Realistic web environment for evaluating agents on real tasks, where the honest success rates live.
- [UI-TARS](https://arxiv.org/abs/2501.12326) - Native GUI agent model, relevant to anyone expecting an agent to operate an interface.
- [Rico](https://www.interactionmining.org/archive/rico) - Mobile app design dataset of screens and hierarchies that much of this research is trained on.

## Reading

- [Figma AI report](https://www.figma.com/reports/ai-2025/) - Survey data on what teams actually do with AI, worth more than anecdote.
- [Smashing Magazine on AI](https://www.smashingmagazine.com/category/ai/) - Practitioner articles on AI in design and front-end work.
- [Laws of UX](https://lawsofux.com/) - Short reference for the heuristics you will be citing in reviews.
- [10 usability heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) - The original list, still the cheapest shared vocabulary for critique.

## Related lists

- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) - Commands, hooks, and workflows for Claude Code.
- [awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers) - Large index of MCP servers by category.
- [awesome-design-systems](https://github.com/alexpate/awesome-design-systems) - Public design systems and style guides.
- [Awesome Design Tools](https://github.com/goabstract/Awesome-Design-Tools) - Broad design tool index, most of it not AI.
- [awesome-a11y](https://github.com/brunopulis/awesome-a11y) - Accessibility resources and tooling.
- [awesome](https://github.com/sindresorhus/awesome) - The list of awesome lists.

## Contributing

Suggestions are welcome. One entry per pull request, the link checked, and a one-line description of what the thing does rather than what it promises. See [contributing.md](contributing.md).

## Who maintains this

[Humbleteam](https://humbleteam.com/) is a digital product design and AI-engineering studio: founded in 2017, working from Prague and Dubai, with 80+ digital awards to the name, including 14 Awwwards wins, a Webby, and a Red Dot. We design digital products for startups and enterprises in fintech, healthtech, sports, and AI, and we build AI infrastructure for design teams - agents, workflows, and skills like the ten listed above.

- What we do with AI for design teams: [humbleteam.com/ai](https://humbleteam.com/ai)
- Our work: [humbleteam.com/work](https://humbleteam.com/work)
- Design and AI writing: [humbleteam.com/blog](https://humbleteam.com/blog)
- LinkedIn: [linkedin.com/company/humbleteam](https://www.linkedin.com/company/humbleteam/)
- Talk to us: [hi@humbleteam.com](mailto:hi@humbleteam.com)

footer: © Falko Richter - This presentation was built *without* AI
slidenumbers: true

* German, Nachfragen gerne auf Englisch
* Es wird aufgezeichnet, Präsentation gibt es am Ende
* Q&A am Ende
  * Florian notiert Themen fürs Q&A
* 90 Minuten, Florian achtet auf die Zeit :)

### Fragen?

---

## About me

* internationale Medieninformatik HTW 🌎
* 16 Jahre IT - crossfunctional IC/EM/Product
	* TIC-mobile/Sinnerschrader/Accenture, Sensorberg (IOT), Kitchenstories 👨‍🍳 Wayfair (🇺🇸 Möbelhandler)
* 35services 🧰 KTG Grundschule 🚸 Berlindroid 🤖
* Lastenräder 🚴‍♂️ Quadrokopter ✈ Podcaster, Papa von 2 👧 

---

## Was kennt ihr schon?

* Welche  AI use cases nutzt ihr bereits (privat)
* Vibe coding?

---

## IT Milestones
* personal computer / internet
* web 2.0
* iPhone
* cloud
* ?

---

# Begriffe

- OpenAI, Anthropic (Firmen)
- ChatGPT, [claude](https://claude.ai/) (Produkte)
- GPT-4, Gemini 2.5 Pro, Claude Sonnet 4, Claude Opus 4.1 (LLMs)

...

---

## vibe coding

# Was ist das eigentlich?

[x.com/karpathy](https://x.com/karpathy/status/1886192184808149383)

"There's a new kind of coding I call "vibe coding", where you fully give in to the vibes, embrace exponentials, and forget that the code even exists."

---

> Vibe Coding bezeichnet eine Art der Softwareentwicklung, bei der nahezu ausschließlich der Prompt eines großen Sprachmodells bedient wird, um den für die Software erforderlichen Quellcode zu generieren.
> 
> 
> Vibe Coding arbeitet mit den Mitteln des Prompt Engineerings. Anders als die qualifizierte Softwareentwicklung, die Überprüfungen und Tests des Quellcodes und des Produkts auf Fehlerfreiheit durch Fachpersonal einschließt, soll Vibe Coding keine Vorkenntnisse oder Ausbildung erfordern.
--  [de.wikipedia.org/wiki/Vibe_Coding](https://de.wikipedia.org/wiki/Vibe_Coding)

---
## vibe coding

### „Reines“ Vibe-Coding: 
In seiner explorativsten Form vertraut der Nutzer vollständig darauf, dass der KI-Output wie beabsichtigt funktioniert. Wie Karpathy es formulierte, ist das so, als würde man „vergessen, dass der Code überhaupt existiert“. Daher eignet sich diese Methode am besten für schnelle Ideenfindung oder für das, was er als „Wochenendprojekte“ bezeichnet, bei denen es vor allem auf Geschwindigkeit ankommt. [cloud.google.com](https://cloud.google.com/discover/what-is-vibe-coding?hl=de)

---

## ~~vibe coding~~ **agentic coding**

### Verantwortungsbewusste KI-gestützte Entwicklung:
"Hier geht es um die praktische und professionelle Anwendung des Konzepts. In diesem Modell fungieren KI-Tools als leistungsstarke Unterstützung oder „Paarprogrammierer“. Die Nutzerin oder der Nutzer gibt der KI Anweisungen, prüft, testet und versteht den generierten Code und übernimmt die volle Verantwortung für das Endprodukt." [cloud.google.com](https://cloud.google.com/discover/what-is-vibe-coding?hl=de)

---

## Für euch ausprobiert: tools

* [Cursor](https://cursor.com/) (VS fork)
* windsurf ([VS fork](https://windsurf.com/editor) mit integration, [plugins](https://windsurf.com/plugins))
* [github CoPilot](https://github.com/features/copilot) (online)
* [cline.bot](https://cline.bot/) (VS code plugin)
* gemini
* notebookLM -> wissensmanagement
   * `35services` [link](https://notebooklm.google.com/notebook/be006e4a-dcd2-4c13-894c-1f165020c52e)
   * `35services Steuern` [link](https://notebooklm.google.com/notebook/2a477e34-a6c9-48ae-b563-e79b01de4a56)
   * `Google and other podcasts` [link](https://notebooklm.google.com/notebook/2c344d3e-8a01-4fc4-a566-9b0c5ffb2cf3)

---

## Für euch ausprobiert: use-cases

* "pure" vibe coding" / "Verantwortungsbewusste KI-gestützte Entwicklung"
* code completion/ review (copilot, gemini, cursor)
* [ADRs](https://github.com/joelparkerhenderson/architecture-decision-record) und RFCs schreiben
* (Security) reviews (`Android -> PHP -> Microservice`)
* Diagramme

Bilder generieren, Bilder bearbeiten (👻)


---

## LLM

* large language model / Sprachmodell
* Programmieren == Sprache
* trainiert mit GIT Verläufen `->` Programmier Prozesse

`LLMs are very good at duplicating solutions to problems that have already been solved. So basic programming patterns are very easy for it to spit out.`

---

> Well.. one obvious reason is that this is what they were trained of, so this is what they excel at. An LLM is essentially a completion algorithm, that must adhere to the same alphabet soup it has swallowed during its training.
-- Asaf Atzmon [beeblebrux.medium.com/llms-are-all-the-vibe-but-whats-next-c653d5b7cae5](https://beeblebrux.medium.com/llms-are-all-the-vibe-but-whats-next-c653d5b7cae5)

---

## Komponenten / wie geht das?
* frontend/app
   * Integrationen
   * MCP
* llm
	* local / remote [Vertex.ai](https://cloud.google.com/vertex-ai?hl=de)...

---

* feedback loop
* multi agent
* plan / act mode
* background mode

---

# Andere tools:
* [goose](https://block.github.io/goose/) (command line)
* [junie von Jetbrains](https://www.jetbrains.com/de-de/junie/) (plugin)
* [claude code](https://claude.com/product/claude-code) (command line)
* [cursor CLI](https://cursor.com/de/docs/cli/overview)
* [cline plugins](https://docs.cline.bot/getting-started/installing-cline) in andere IDEs (VS Code, JetBrains IDEs)

---

## MCP

* [https://claude.ai/share/d5385d25-9238-4f20-afd8-1835ddf5e909](https://claude.ai/share/d5385d25-9238-4f20-afd8-1835ddf5e909)
* [server-concepts#how-tools-work](https://modelcontextprotocol.io/docs/learn/server-concepts#how-tools-work)

```
/**
   * Returns comprehensive tool definitions optimized for AI agent interaction.
   * Tools are categorized and include detailed usage guidance, examples, and workflow patterns.
   */
  listTools(): Promise<{ tools: MCPToolDto[] }> 

  async callTool(name: string, args: any): Promise<any>
```
* [github.com/falkorichter/fairsplit/blob/main/src/mcp/mcp.service.ts#L33](https://github.com/falkorichter/fairsplit/blob/main/src/mcp/mcp.service.ts#L33)


---

## case study 1: Chrome plugin bauen

---
## case study 1: Chrome plugin bauen
#### product briefing
[https://github.com/falkorichter/agentic-archive.is-ifier](https://github.com/falkorichter/agentic-archive.is-ifier)



* [https://github.com/falkorichter/agentic-archive.is-ifier/commit/1e1de4979801079e9404a4297a7b4aeedc4e520b](https://github.com/falkorichter/agentic-archive.is-ifier/commit/1e1de4979801079e9404a4297a7b4aeedc4e520b) intial README

---
## case study 1: Chrome plugin bauen
#### github copilot
   * pull request [https://github.com/falkorichter/agentic-archive.is-ifier/pull/2](https://github.com/falkorichter/agentic-archive.is-ifier/pull/2)
   * [https://github.com/falkorichter/agentic-archive.is-ifier/pull/2/agent-sessions/63746a6c-0dde-4a6f-a928-87fad3e00952](https://github.com/falkorichter/agentic-archive.is-ifier/pull/2/agent-sessions/63746a6c-0dde-4a6f-a928-87fad3e00952)

---
   
* "Now let me test the extension by taking a screenshot using a browser to verify it works correctly. First, let me open the extension in a browser:" [deeplink](https://github.com/falkorichter/agentic-archive.is-ifier/pull/2/agent-sessions/63746a6c-0dde-4a6f-a928-87fad3e00952#:~:text=Now%20let%20me%20test,playwright%2Dmcp%2Dserver%2Dbrowser_navigate)
* "Now let me create a basic icon. I'll create a simple PNG with "is!" text:"
* "Now let me test the extension by taking a screenshot using a browser to verify it works correctly. First, let me open the extension in a browser:"

---

```text
Error: page.goto: net::ERR_BLOCKED_BY_CLIENT at file:///home/runner/work/agentic-archive.is-ifier/agentic-archive.is-ifier/test.html Call log:

navigating to "file:///home/runner/work/agentic-archive.is-ifier/agentic-archive.is-ifier/test.html", waiting until "domcontentloaded"
```

---

## case study 1: Chrome plugin bauen
### tests bauen

Tests waren von Anfang an dabei 💪

`Can we setup github CI for the project please to ensure tests are run as part of the PR` [issues/3](https://github.com/falkorichter/agentic-archive.is-ifier/issues/3)
* [tests/test-runner-headless.js](https://github.com/falkorichter/agentic-archive.is-ifier/pull/4/files#diff-445db4a234ffa5f8a0a5822dc73e2b4d75ff94b4771ecb1ba92e1a975c38baaf)
* [/main/tests/test-functions.js#L322](https://github.com/falkorichter/agentic-archive.is-ifier/blob/main/tests/test-functions.js#L322)
* [live](file:///Users/falkorichter/Documents/workspaces/open%20source/agentic-archive.is-ifier/tests/test.html) 


---

## Haluzinationen

[Beispiel](https://github.com/falkorichter/agentic-archive.is-ifier/pull/43/files#diff-b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5R255)

[https://github.com/falkorichter/agentic-archive.is-ifier/issues/34](https://github.com/falkorichter/agentic-archive.is-ifier/issues/34)

---

## copilot suggests

[https://github.com/falkorichter/agentic-experiences/pull/2#issuecomment-3192211640](https://github.com/falkorichter/agentic-experiences/pull/2#issuecomment-3192211640) copilot actions

> @falkorichter 👋 This repository doesn't have [Copilot instructions](https://docs.github.com/enterprise-cloud@latest/copilot/how-tos/configure-custom-instructions/add-repository-instructions?tool=webui). With Copilot instructions, > I can understand the repository better, work faster and produce higher quality PRs.

> I can generate a .github/copilot-instructions.md file for you automatically. Click [here](https://github.com/falkorichter/agentic-experiences/issues/new?title=✨+Set+up+Copilot+instructions&body=Configure%20instructions%20for%20this%20repository%20as%20documented%20in%20%5BBest%20practices%20for%20Copilot%20coding%20agent%20in%20your%20repository%5D%28https://gh.io/copilot-coding-agent-tips%29%2E%0A%0A%3COnboard%20this%20repo%3E&assignees=copilot) to open a pre-filled issue and assign it to me. I'll write the instructions, and then tag you for review.



---


## 2 fairsplit

https://github.com/tobiasheine/fairsplit/pull/40

> * 🎯 Product Agent: Requirements gathering and story grooming
> * 💻 Development Agent: Code implementation and architecture
> * 🧪 Testing Agent: Quality assurance and test creation
> * 🚀 DevOps Agent: Deployment and infrastructure management
> * 📋 Orchestrator Agent: Workflow coordination and process enforcement
[https://github.com/tobiasheine/fairsplit/blob/07ab4fd678a839bace397cf9509c10322ea6b605/CASE_STUDY_STORY.md#the-multi-agent-architecture-solution](the-multi-agent-architecture-solution)

---
### list of case studies
* huge refactoring, repetitive tasks
* KI meeting notes + notebookLM
* security analysis kotlin/PHP/java
* frage vom Kollegen
* ...

---
### meine Erfahrungen

* Skepsis (Halluzinationen)
* WOW 🤯 ([TiB_Verein](https://github.com/falkorichter/TiB_Verein)) - WOW 😳
* Super Ergänzung an extrem vielen Ecken
* "Your Junior developer" - oder ein [Staff Bug Fixing Engineer](https://medium.com/for-self-taught-developers/i-spent-6-years-as-a-senior-developer-then-ai-fixed-my-bug-in-15-minutes-thats-when-i-knew-i-94d9fef9990a) [archive.is](https://archive.is/U8F3z)

---

## Q&A

---

### Overflow

* `Mermaid-Diagramme`: [cursor.com/de/docs/configuration/tools/mermaid-diagrams](https://cursor.com/de/docs/configuration/tools/mermaid-diagrams)

---

> In an AI-driven world, staying comfortable is the riskiest career move you can make. 
-- ([source](https://medium.com/for-self-taught-developers/i-spent-6-years-as-a-senior-developer-then-ai-fixed-my-bug-in-15-minutes-thats-when-i-knew-i-94d9fef9990a) [archive.is](https://archive.is/U8F3z))


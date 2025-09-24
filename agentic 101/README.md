
* German, nachfragen auf English
* Q&A am Ende
  * Florian notiert Zwischenfragen fürs Ende wenn sie adhoc beantwortet

## About me

* was habe ich mit AI tools gemacht:
   * details unten
   * 

## What do you expect
* Erwartungsabfrage
* Was ist vibe coding
* "Ich weiß gar nicht worum es geht"

## my experience with AI tools

* goose
* Cursor
* windsurf
* github CoPilot
* notebookLM -> wissensmanagement
   * https://notebooklm.google.com/notebook/be006e4a-dcd2-4c13-894c-1f165020c52e `35services`
   * https://notebooklm.google.com/notebook/2a477e34-a6c9-48ae-b563-e79b01de4a56 `35services Steuern`
   * https://notebooklm.google.com/notebook/2c344d3e-8a01-4fc4-a566-9b0c5ffb2cf3 `Google and other podcasts`
   * 
..

plan / act mode

## components
* frontend/app
   * cursor 
* llm, local / Vertex.ai
   * `warum können die gut programmieren`
* feedback loop
* multi agent

## MCP

https://claude.ai/share/d5385d25-9238-4f20-afd8-1835ddf5e909
https://github.com/tobiasheine/fairsplit/blob/main/src/mcp/mcp.service.ts#L33

```
/**
   * Returns comprehensive tool definitions optimized for AI agent interaction.
   * Tools are categorized and include detailed usage guidance, examples, and workflow patterns.
   */
  listTools(): Promise<{ tools: MCPToolDto[] }> 

  private requireAuth(): string 

  async callTool(name: string, args: any): Promise<any>
```

## 1 case study plugin bauen

https://github.com/tobiasheine/fairsplit/pull/40

> * 🎯 Product Agent: Requirements gathering and story grooming
> * 💻 Development Agent: Code implementation and architecture
> * 🧪 Testing Agent: Quality assurance and test creation
> * 🚀 DevOps Agent: Deployment and infrastructure management
> * 📋 Orchestrator Agent: Workflow coordination and process enforcement
[https://github.com/tobiasheine/fairsplit/blob/07ab4fd678a839bace397cf9509c10322ea6b605/CASE_STUDY_STORY.md#the-multi-agent-architecture-solution](the-multi-agent-architecture-solution)

### list of case studies
* huge refactoring, repetitive tasks
* KI meeting notes + notebookLM
* security analysis kotlin/PHP/java
* frage vom Kollegen
* ...

## Q&A


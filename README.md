# PM Review Skill

[English](README.md) | [中文](README-zh.md)

A professional Product Manager page review skill for AI assistants that evaluates web pages or design screenshots using a comprehensive seven-dimension framework.

## Compatible Agents

This skill is designed to work with MCP-compatible AI assistants:

| Agent | Native Support | Notes |
|-------|----------------|-------|
| **Claude Code** | ✅ Yes | Full `.skill` format support |
| **Cursor** | ⚠️ Partial | Requires `.clinerules` adaptation |
| **Continue** | ⚠️ Partial | Requires config adaptation |
| **Cline** | ⚠️ Partial | Manual prompt injection |
| **Other MCP Agents** | ✅ Compatible | If MCP servers are available |

## Features

- **Dual Input Support**: Review via URL or design screenshot
- **Two Review Modes**: Quick review (5 min) or Deep review (30 min)
- **Seven-Dimension Framework**: Strategic goals, UX, functionality, metrics, performance, competition, operations
- **Structured Output**: Professional review reports with prioritized recommendations
- **MCP Integration**: Enhanced analysis with compatible MCP servers

## Installation

### Claude Code (Native)

1. Copy the skill file to your skills directory:
```bash
cp pm-review-skill.skill ~/.claude/skills/
```

2. Or install from extracted directory:
```bash
mkdir -p ~/.claude/skills/pm-review-skill
cp -r pm-review-skill/* ~/.claude/skills/pm-review-skill/
```

### Cursor / Continue / Other Agents

**Option 1: Manual Prompt Injection**

Add to your project's `.clinerules` or prompt template:

```
You are a PM review expert. Use the following framework:
[Copy content from pm-review-skill/SKILL.md]
```

**Option 2: Custom Instructions**

Configure your agent's system prompt with:
1. The seven-dimension framework from `dimensions.md`
2. Review workflow from `quick-review.md` or `deep-review.md`
3. Output templates from `templates.md`

**Option 3: MCP Server Setup**

For enhanced capabilities, configure MCP servers:

```json
{
  "mcpServers": {
    "web-reader": {
      "command": "npx",
      "args": ["-y", "@zengwenliang/web-reader-mcp"]
    },
    "zai-mcp": {
      "command": "npx",
      "args": ["-y", "zai-mcp-server"]
    }
  }
}
```

## Usage

### Trigger the Skill

The skill activates when you ask your AI assistant to:
- Review a page or design
- Analyze a screenshot
- Evaluate a UI/UX design
- Conduct PM review or product review

### URL Review

Provide a webpage URL for functional review:

```
Please review https://example.com
```

### Screenshot Review

Provide a design image for visual and interaction review:

```
Please review this design screenshot: [attach image]
```

## Seven-Dimension Framework

| Dimension | Key Question | Focus Areas |
|-----------|--------------|-------------|
| **1. Strategic Goals** | Why does this page exist? | Business alignment, value proposition, user problems |
| **2. User Experience** | Can users complete tasks smoothly? | Information hierarchy, interaction paths, state coverage |
| **3. Functionality** | Are features complete? | Core functions, content quality, error handling |
| **4. Data & Metrics** | Is impact measurable? | Analytics, KPI alignment, A/B testing points |
| **5. Technical Performance** | Is it technically feasible? | Load speed, compatibility, accessibility |
| **6. Market & Competition** | How does it compare? | Differentiation, user habits, compliance |
| **7. Operations** | Is it maintainable? | Modularity, extensibility, operational costs |

## Review Modes

### Quick Review (5 minutes)

For initial screening and fast assessment:
- Core problems identification
- Optimization suggestions
- Highlights and strengths

### Deep Review (30 minutes)

For important pages requiring comprehensive analysis:
- Complete diagnostic report
- Three solution approaches (Progressive / Restructure / Ideal)
- Execution plan with metrics

## Output Structure

Every review includes:

1. **Problem Classification**: Critical (P0) / Experience (P1) / Optimization (P2)
2. **Three Solution Sets**: Progressive optimization / Structural redesign / Ideal solution
3. **Priority Ranking**: Impact × Effort matrix
4. **Metrics**: Verifiable success criteria

## Scoring Standard

| Total Score | Rating | Recommendation |
|-------------|--------|----------------|
| 60-70 | Excellent | Maintain and strengthen |
| 45-59 | Good | Targeted optimization |
| 30-44 | Average | Systematic improvement |
| <30 | Needs Improvement | Redesign |

## Reference Documentation

- `dimensions.md` - Seven-dimension scoring criteria
- `quick-review.md` - 5-minute quick review process
- `deep-review.md` - 30-minute deep review process
- `templates.md` - Review report templates

## MCP Server Integration (Optional)

For enhanced screenshot analysis, consider installing:

| MCP Server | Purpose | Compatibility |
|-------------|---------|----------------|
| **ZAI MCP Server** | Advanced image analysis | All MCP-compatible agents |
| **Web Reader MCP** | Web content extraction | All MCP-compatible agents |
| **MiniMax Image** | Alternative image analysis | All MCP-compatible agents |
| **4.5v Vision** | High-quality image analysis | All MCP-compatible agents |

Configure in your agent's MCP settings file.

## Agent-Specific Notes

### Claude Code
- Native `.skill` format support
- Automatic skill activation based on triggers
- MCP server configuration in `~/.claude/mcp_settings.json`

### Cursor
- Add to `.clinerules` file at project root
- May require manual activation via custom instructions
- MCP support through Cursor settings

### Continue
- Add to Continue's custom instructions
- Configure MCP servers in Continue settings
- Best used with Continue Dev extension

### Cline
- Manual prompt injection recommended
- Add custom instructions to Cline settings
- Limited MCP server support

## License

MIT License

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## Acknowledgments

Designed with multi-agent compatibility in mind. Works best with AI assistants that support:
- MCP (Model Context Protocol) servers
- Custom instruction injection
- File-based skill/loading mechanisms

# References Index

This directory contains extended documentation loaded on-demand to keep SKILL.md under 5k tokens.

## Files

- **domain-context.md** - Team background, metrics definitions, stakeholders, writing style
- **mcp-integration.md** - MCP tool usage examples, troubleshooting, common patterns
- **examples/** - Sample newsletters and edge cases
  - `simple-newsletter.md` - Basic weekly update example
  - `quarterly-review.md` - Extended quarterly summary example

## When to Reference

Claude will automatically reference these files when:
- User asks "What does ABAC stand for?" or needs team context → `domain-context.md`
- MCP tool call fails or needs examples → `mcp-integration.md#troubleshooting`
- User wants to see sample outputs → `examples/`

## Customization Instructions

**👉 You MUST update `domain-context.md` with:**
- Your team's mission and goals
- Key metrics your stakeholders care about
- Writing style preferences
- Common acronyms and terminology

**👉 Optionally update `mcp-integration.md` with:**
- Custom MCP tool configurations
- Your organization's specific tool usage patterns
- Troubleshooting solutions specific to your setup

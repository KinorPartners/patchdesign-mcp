# PatchDesign.AI MCP server

PatchDesign.AI designs custom patches in your AI chat. Describe a patch for
your team, troop, club, department, event or brand, and the server generates
a production-ready design and shows it in the chat. Ask for changes in plain
words, ask what a run would cost, and get a link that opens your design on
[patchdesign.ai](https://patchdesign.ai) to order it.

- **Server:** `https://patchdesign.ai/api/mcp` (remote, Streamable HTTP)
- **Nothing to configure:** no API key and no sign-in to start
- **Listing:** `ai.patchdesign/patch-designer` in the
  [MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=ai.patchdesign)
- **Setup for every chat and editor:** https://patchdesign.ai/connect
- **What it does, in plain words:** https://patchdesign.ai/mcp

This repository holds the server's documentation. The server itself runs on
patchdesign.ai; its source lives in PatchDesign.AI's private codebase.

## What the server does

| Tool | What it does |
| --- | --- |
| `quote_patch` | Prices embroidered, woven, chenille, printed and PVC patches from the live production price table, by size and quantity. |
| `design_patch` | Generates a patch design from a description, or from the URL of a logo, sketch or photo. Takes about 15 to 30 seconds. |
| `edit_patch` | Changes a design in plain words ("make the border gold"). Earlier versions stay. |
| `order_link` | A link that opens the design on patchdesign.ai with the type, size and quantity set. Nothing is ordered or charged from the chat. |
| `sign_in_link` | Connects a PatchDesign.AI account, which saves your designs to it. |

In clients that draw MCP Apps (GitHub Copilot in VS Code, ChatGPT, Claude,
Cursor) a design shows as a card: the preview, its design reference (D-...),
type and size, and an order button. Other clients show the preview image and
the links, or the result's text and links.

Previews carry a light PatchDesign.AI mark; the clean production file comes
with the order. Each chat can make up to ten designs before you connect an
account.

## Configure

The server needs no credentials. Add it by URL wherever your client takes a
remote MCP server; https://patchdesign.ai/connect has the menu path for each
one, checked against the vendors' help pages.

**GitHub Copilot in VS Code:** add the server to `.vscode/mcp.json` in a
workspace (or to your user `mcp.json` through `MCP: Open User Configuration`):

```json
{
  "servers": {
    "patchdesign": {
      "type": "http",
      "url": "https://patchdesign.ai/api/mcp"
    }
  }
}
```

Then start it from the MCP: List Servers command, or from the server's
CodeLens, and check that Copilot's Agent mode shows five tools.

**Claude Code:**

```bash
claude mcp add --transport http patchdesign https://patchdesign.ai/api/mcp
```

**Cursor:** add the server to `~/.cursor/mcp.json` (every project) or
`.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "patchdesign": {
      "url": "https://patchdesign.ai/api/mcp"
    }
  }
}
```

**ChatGPT, Claude, Gemini, Grok, Perplexity, Le Chat:** add a custom
connector with the server URL; the steps for each are on
https://patchdesign.ai/connect.

## Use

Ask in plain words. Things to try:

- Design a 3 inch embroidered patch for Troop 42 with an eagle in navy and gold.
- How much are 100 embroidered 3 inch patches?
- Make the border gold and change the text to EST. 2026.
- I want to order 50 of this one.

A design takes about 15 to 30 seconds. Each version gets its own preview and
D- number. To change a design in a later turn, refer to it by its D- number
in the same chat. When you want the patches made, the order link opens the
design on patchdesign.ai, where you review the order and pay. Nothing is
ordered or charged from the chat, and no delivery date is promised there:
production takes about 10 business days after artwork approval, plus shipping.

After ten designs in a chat the server offers a sign-in link. Connecting a
PatchDesign.AI account keeps the designs coming and saves them to the account
at https://patchdesign.ai/my-designs.

## Privacy and terms

Designs made through the chat are kept with the conversation that made them,
so a later turn can change or order them. PatchDesign.AI's
[privacy policy](https://patchdesign.ai/privacy-policy) (Section 3A covers
the AI-chat connector) and [terms](https://patchdesign.ai/terms) apply.

## Support

service@patchdesign.ai, or https://patchdesign.ai/contact.

## License

The documentation in this repository is under the MIT License (see
`LICENSE`). The PatchDesign.AI name and logo belong to Kinor LLC.

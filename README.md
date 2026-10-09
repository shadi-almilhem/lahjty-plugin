# Lahjty plugin

Make social media ads for the products you sell, in Arabic and English, without leaving your AI assistant.

Share your store website or a product page. Lahjty reads it, asks a few quick questions (which product, the offer or price, the platform, the language or Arabic dialect, your product photo and logo), tells you the credit cost, then creates ad images, captions and optional voiceovers. Ask for changes like "make the background white" and Lahjty edits the image you already made.

The plugin connects your assistant to the hosted Lahjty MCP server at `https://www.lahjty.com/mcp` and adds the `ads` skill, which guides the whole workflow.

Full setup guide for every app: https://www.lahjty.com/en/mcp (Arabic: https://www.lahjty.com/ar/mcp)

## Install

### Claude Code

Inside Claude Code:

```text
/plugin marketplace add shadi-almilhem/lahjty-plugin
/plugin install lahjty@lahjty
```

Or from a terminal:

```bash
claude plugin marketplace add shadi-almilhem/lahjty-plugin
claude plugin install lahjty@lahjty
```

Then run `/mcp`, choose Lahjty and sign in with your Lahjty account in the browser.

Make ads with the skill, or just ask:

```text
/lahjty:ads https://example-store.com
```

```text
make ads for mystore.com
```

### Codex

```bash
codex plugin marketplace add shadi-almilhem/lahjty-plugin
codex plugin add lahjty@lahjty
```

You can also open `/plugins` in Codex and install Lahjty from the `lahjty` marketplace. Start a new session after installing. To connect only the MCP server:

```bash
codex mcp add lahjty --url https://www.lahjty.com/mcp
codex mcp login lahjty
```

### ChatGPT

Lahjty is not listed in the ChatGPT plugin directory yet. Until it is, add it as a custom MCP server on ChatGPT on the web:

1. Go to https://chatgpt.com/plugins, select the plus button, then **Add custom MCP server**.
2. Name it Lahjty, enter `https://www.lahjty.com/mcp` under **Connection** and choose OAuth. Select **I understand and want to continue**, then **Create as a plugin**.
3. Install the plugin, start a new chat, type `@` and pick Lahjty. Sign in to Lahjty when asked.

Workspace settings can limit custom MCP servers.

### Claude on the web or desktop

Open **Customize > Connectors**, select **+ Add**, then **Add custom connector**. Name it Lahjty, paste `https://www.lahjty.com/mcp`, select **Continue**, then **Add** and **Connect**. On Team and Enterprise plans an Owner adds it first under **Organization settings > Connectors**.

### Cursor, VS Code and other apps

The setup guide has one-click install links for Cursor and VS Code, plus configs for other MCP apps: https://www.lahjty.com/en/mcp#connect

## Accounts and credits

- Any Lahjty account can connect with browser sign-in, including free accounts.
- Reading a website, browsing the Ad Library, uploading your photos and checking your balance are free.
- Images, edits, captions, dialect conversion and voiceovers use credits from your Lahjty account. Lahjty states the cost before each paid step.
- Current credit costs and plans: https://www.lahjty.com/en/mcp#capabilities and https://www.lahjty.com/en/pricing
- Developer API keys (for headless setups) need a plan with API access.

## Privacy

- Lahjty reads a website only when you share it in the chat.
- Lahjty never posts or publishes to your social accounts. It creates drafts that you review, download and post yourself.
- Uploaded photos are used for your request and expire after 24 hours. Finished results are saved in your Lahjty history.
- Disconnect any time from https://www.lahjty.com/en/oauth/connections and remove the plugin from your app (`claude plugin uninstall lahjty@lahjty` or `codex plugin remove lahjty@lahjty`).

Privacy policy: https://www.lahjty.com/en/privacy-policy
Terms of service: https://www.lahjty.com/en/terms-of-service

## Support

- Contact: https://www.lahjty.com/en/contact or contact@lahjty.com
- Issues with this plugin: open an issue in this repository.

## Repository layout

```text
.claude-plugin/marketplace.json     Claude Code marketplace
.agents/plugins/marketplace.json    Codex marketplace
plugins/lahjty/
  .claude-plugin/plugin.json        Claude Code plugin manifest
  .mcp.json                         Claude Code MCP server (HTTP, OAuth)
  plugin.json                       Agent Plugins manifest (OpenAI)
  mcp.json                          Agent Plugins MCP server (streamable HTTP)
  skills/ads/                       The ads workflow skill
  assets/                           Icon and logo
```

The plugin contains no code that runs on your machine. All generation happens on the hosted Lahjty server after you sign in.

## License

MIT. See [LICENSE](LICENSE).

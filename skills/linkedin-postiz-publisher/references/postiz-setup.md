# Set up Postiz (about 5 minutes)

Postiz is an open-source social media scheduler. Use the hosted version at postiz.com or self-host it for free.

## Hosted

1. Create an account at https://postiz.com.
2. Connect LinkedIn: **Add Channel** → **LinkedIn** → authorize.
3. Go to **Settings** → **Public API** and copy your API key.
4. Save it as an environment variable on your computer, not in the chat. Add this line to `~/.zshrc` (Mac) or `~/.bashrc` (Linux):
   ```bash
   export POSTIZ_API_KEY="paste-your-key-here"
   ```
   Then open a new terminal and restart Claude.
5. Test it. Ask Claude: **"List my Postiz channels."** You should see your LinkedIn account.

Prefer a file? Copy `.env.example` to `.env` in this folder and fill it in. `.env` is git-ignored.

## Self-hosted (free)

1. Follow https://docs.postiz.com/installation (Docker is the usual route).
2. Connect LinkedIn in your own Postiz dashboard.
3. Set both variables:
   ```bash
   export POSTIZ_API_KEY="key-from-your-instance"
   export POSTIZ_API_URL="https://your-domain/api/public/v1"
   ```
4. Test with **"List my Postiz channels."**

## Using Claude on the web or Desktop app?

There's no terminal to hold the key. The skills still work: every post comes back as a copy-ready block, and the publisher saves it to `post-ready-to-paste.txt`. Or connect the official Postiz MCP server as a custom connector if your plan supports it.

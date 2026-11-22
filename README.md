# Clipscript MCP

Transcripts for YouTube, TikTok, Instagram Reels, Facebook and X videos: paste a link, get the transcript with timestamps.

get_transcript transcribes one link and bulk_transcripts up to 10. list_channel_videos lists the latest videos of a YouTube channel, TikTok profile or Instagram profile. list_history, get_saved_transcript and export_transcript reopen saved transcripts as TXT, SRT, VTT or JSON, and get_usage shows your plan allowance. Every transcript is cached by video, and reopening one from your history is free.

## Remote MCP

Use **https://cliptranscript.app/mcp** (streamable HTTP) in a client that supports remote MCP. Sign in with OAuth 2.1 (dynamic client registration; metadata at `https://cliptranscript.app/.well-known/oauth-authorization-server`), or on Pro and Scale send an API key as `Authorization: Bearer cs_live_…` (create keys at https://cliptranscript.app/app/developers/).

## Claude Desktop and other stdio clients

Requires Node.js 22 or newer. Add this configuration:

```json
{
  "mcpServers": {
    "clipscript": {
      "command": "npx",
      "args": [
        "-y",
        "clipscript-mcp"
      ]
    }
  }
}
```

Or install the `.mcpb` file from [Releases](https://github.com/cliptranscript/mcp-server/releases) in your desktop client's Extensions settings. The connector opens your browser for sign-in.

## Plans

Free account: 5 transcripts a day (copy and TXT). Creator $9/month: 400 a month with SRT, VTT, JSON, bulk and channel import. Pro $19/month: 1,500 a month plus API keys. Scale $49/month: 4,000 a month.

## Privacy and permissions

Your Clipscript password is not requested by this package. The pinned [mcp-remote](https://www.npmjs.com/package/mcp-remote) bridge handles OAuth, PKCE and local token storage. It connects only to the fixed endpoint above; command-line endpoint overrides are not supported. OAuth tokens are stored locally by mcp-remote and should be treated as credentials. See the [privacy policy](https://cliptranscript.app/privacy/) and [terms](https://cliptranscript.app/terms/).

## Development and publishing

Run `npm ci` and `npm test`. GitHub Actions publishes a new package version using the organization’s `NPM_TOKEN` secret, then builds and releases the desktop bundle. Keep package.json, manifest.json, server/config.json and server.json versions aligned.

[Website](https://cliptranscript.app) · [Issues](https://github.com/cliptranscript/mcp-server/issues)

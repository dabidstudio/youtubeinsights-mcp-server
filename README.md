

# YouTube Insights MCP Server
[![smithery badge](https://smithery.ai/badge/youtube-insights-mcp-server)](https://smithery.ai/server/youtube-insights-mcp-server)

A Model Context Protocol (MCP) server that enables insight extraction from YouTube videos, including subtitle parsing, keyword-based video discovery, and channel info retrieval.

## Features

- Extract transcripts from YouTube videos (multi-language)
- Search videos by keyword and fetch metadata (views, likes, thumbnails, etc.)
- Retrieve channel info and latest videos from any YouTube video URL
- FastMCP-based server integration for easy deployment
- MCP Tools for seamless agent workflows

## Installation


### Using uvx (recommended)

When using [`uvx`](https://docs.astral.sh/uv/guides/tools/), no specific installation is needed.

Add the following configuration to your MCP settings file (e.g., `cline_mcp_settings.json` for Claude Desktop):

```json
{
  "mcpServers": {
    "youtubeinsights": {
      "command": "uvx",
      "args": ["youtubeinsights-mcp-server"],
      "env": {
        "YOUTUBE_API_KEY": "your-api-key",
      }
    }
  }
}
```

### Development Installation

1. Clone this repository
2. Install dependencies:
   ```bash
   uv venv
   ```
3. Copy `.env.example` to `.env` and fill in your youtube data api credentials

```json
{
  "mcpServers": {
    "youtubeinsights": {
      "command": "uv",
      "args": [
        "--directory",
        "path/to/youtubeinsights-mcp-server",
        "run",
        "youtubeinsights-mcp-server"
      ],
      "env": {
        "YOUTUBE_API_KEY": "your-api-key",
      }
    }
  }
}
```

## Available MCP Tools

- `get_youtube_transcript`: Extract full transcript (subtitles) from a YouTube video URL (supports `ko`, `en`)
- `search_youtube_videos`: Search for videos on YouTube by keyword and retrieve key metadata
- `get_channel_info`: Get channel metadata and recent uploads based on any YouTube video URL

## Sample MCP Tool Descriptions

```json
{
  "tool": "get_youtube_transcript",
  "description": "Extract subtitles from a given YouTube video URL."
}
```

```json
{
  "tool": "search_youtube_videos",
  "description": "Search videos by keyword and return metadata including views, likes, and thumbnails."
}
```

```json
{
  "tool": "get_channel_info",
  "description": "Retrieve channel info (title, subscriber count, latest uploads) based on a video URL."
}
```


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

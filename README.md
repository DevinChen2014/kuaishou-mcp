# 快手 MCP | Kuaishou MCP | Kwai MCP

This public repository provides public connection docs and MCP metadata for a hosted 快手 MCP / Kuaishou MCP / Kwai MCP service by SocialDataX.

If you are looking for a 快手 MCP, Kuaishou MCP, or Kwai MCP for social media research workflows, this repository includes:

- public MCP metadata and client configuration examples
- the hosted `streamable-http` endpoint for clients that support remote MCP
- an `mcp-remote` fallback example for command/stdio-only MCP clients

The business implementation is privately hosted. This repository exposes only the public connection surface for read-only social media intelligence workflows.

## Search Aliases

Common search phrases for this MCP service:

- `快手 MCP`
- `快手 数据 MCP`
- `快手 热榜 MCP`
- `快手 作品 MCP`
- `快手 评论 MCP`
- `快手 达人 MCP`
- `Kuaishou MCP`
- `Kuaishou data MCP`
- `Kuaishou hot list MCP`
- `Kuaishou work research MCP`
- `Kuaishou comments MCP`
- `Kuaishou creator MCP`
- `Kwai MCP`
- `Kwai data MCP`

## Service

- Hosted MCP endpoint: `https://mcp.52choujiang.com/kuaishou/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website: <https://socialdatax.com>
- Registry name: `com.52choujiang/kuaishou-insights`
- Future registry name: `com.socialdatax/kuaishou-insights`
- Current public capability version: `0.1.0`

## Platform MCP

Use the hosted `streamable-http` endpoint directly from clients that support authenticated remote MCP. For clients that only support command/stdio MCP servers, use `mcp-remote` as a local compatibility proxy.

## Read-Only Scope

This MCP service is designed for read-only social media intelligence workflows. It does not provide account login, posting, editing, liking, commenting, or other account actions.

Supported workflows include:

- Read the Kuaishou / 快手 short-video hot list.
- Search Kuaishou works by natural-language keyword with pagination.
- Resolve a Kuaishou work page link, short link, or share text into structured work details.
- Read work details when the caller already has a `photo_id`.
- Fetch paginated first-level comments for comment analysis.
- Fetch paginated replies under a first-level comment.
- Read creator profile data from a profile link, short link, share text, or `user_id`.
- Fetch creator work lists from a profile link, short link, share text, or `user_id`.

## Tools

| Tool | Public purpose |
| --- | --- |
| `kuaishou_get_hot_search_list` | Get the current Kuaishou / 快手 short-video hot list. |
| `kuaishou_search_videos` | Search Kuaishou works by natural-language keyword with optional paging. |
| `kuaishou_get_video_detail_by_photo_id` | Fetch structured work details when the caller already has a `photo_id`. |
| `kuaishou_get_video_detail_by_url` | Resolve a Kuaishou work page link, short link, or share text into structured work details. |
| `kuaishou_get_video_comments_by_photo_id` | Fetch paginated first-level comments when the caller already has a `photo_id`. |
| `kuaishou_get_video_comments_by_url` | Fetch paginated first-level comments directly from a Kuaishou work page link, short link, or share text. |
| `kuaishou_get_video_comment_replies_by_comment_id` | Fetch paginated replies under a first-level comment by `photo_id` and `comment_id`. |
| `kuaishou_get_user_info_by_user_id` | Fetch creator profile data when the caller already has a `user_id`. |
| `kuaishou_get_user_info_by_profile_url` | Resolve a Kuaishou profile link, short link, or share text into creator profile data. |
| `kuaishou_get_user_posted_videos_by_user_id` | Fetch a paginated list of works published by a creator when the caller already has a `user_id`. |
| `kuaishou_get_user_posted_videos_by_profile_url` | Fetch a paginated list of works published by a creator from a profile link, short link, or share text. |

## Quick Start

For clients that support authenticated `streamable-http`, use the hosted endpoint directly:

```json
{
  "mcpServers": {
    "socialdatax-kuaishou": {
      "type": "streamable_http",
      "url": "https://mcp.52choujiang.com/kuaishou/mcp",
      "headers": {
        "Authorization": "Bearer <SOCIALDATAX_API_KEY>"
      }
    }
  }
}
```

A ready-to-copy example is available in [`examples/streamable_http_config.json`](examples/streamable_http_config.json).

For command/stdio-only MCP clients, use `mcp-remote`:

```json
{
  "mcpServers": {
    "socialdatax-kuaishou": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://mcp.52choujiang.com/kuaishou/mcp",
        "--header",
        "Authorization: Bearer <SOCIALDATAX_API_KEY>"
      ]
    }
  }
}
```

Claude Code can use remote HTTP directly:

```bash
claude mcp add --transport http --header "Authorization: Bearer <SOCIALDATAX_API_KEY>" socialdatax-kuaishou https://mcp.52choujiang.com/kuaishou/mcp
```

Claude Desktop should use its remote MCP / Connectors UI when available. If a local configuration file in your version only supports command/stdio servers, use the `mcp-remote` fallback.

## Client Examples

Configuration examples are available in [examples](examples/):

- [Command/stdio fallback config](mcp.json)
- [Claude Desktop fallback config](examples/claude_desktop_config.json)
- [Cursor remote HTTP config](examples/cursor_mcp.json)
- [Codex remote HTTP config](examples/codex_config.toml)
- [Direct streamable HTTP config](examples/streamable_http_config.json)

## API Key

Request or manage API access from the product website:

<https://socialdatax.com>

Use the key as a Bearer token in the `Authorization` request header. Do not commit real API keys to code, docs, issues, or screenshots.

## Directory Metadata

Public metadata files in this repository:

- [server-card.json](server-card.json): directory-oriented metadata for the hosted service. Official MCP Registry publishing uses the private source repo's `registry/kuaishou/server.json` for the current `com.52choujiang/kuaishou-insights` entry.
- [mcp.json](mcp.json): generic command/stdio fallback config using `mcp-remote`.
- [glama.json](glama.json): Glama repository ownership metadata.
- [SUBMISSION_CHECKLIST.md](SUBMISSION_CHECKLIST.md): checklist for MCP directory submissions.

## License

The files in this public repository are released under the MIT License. The license covers the public documentation and configuration examples in this repository only. It does not cover the managed service implementation, hosted infrastructure, or any private backend code outside this repository.

# MCP Directory Submission Checklist

Use this checklist before syncing this listing to the public Kuaishou MCP repository, submitting it to MCP directories, or updating a directory entry.

## Public Repository

- Primary repository name: `kuaishou-mcp`
- Fallback repository name if unavailable: `kuaishou-socialdatax-mcp`
- Repository URL after creation: `https://github.com/DevinChen2014/kuaishou-mcp`
- Repository description: `快手 MCP / Kuaishou MCP / Kwai MCP by SocialDataX for hot list, work search, work details, comments, comment replies, creator profiles, and creator works.`
- Suggested repository topics: `mcp`, `mcp-server`, `kuaishou`, `kuaishou-mcp`, `kuaishou-data`, `kwai`, `kwai-mcp`, `short-video`, `socialdatax`, `social-insights`, `marketing-research`, `comment-analysis`, `creator-analytics`
- Root README title: `快手 MCP | Kuaishou MCP | Kwai MCP`
- Product: `SocialDataX` / `社媒数据助手`
- Website: `https://socialdatax.com`
- Registry name: `com.52choujiang/kuaishou-insights`
- Future registry name: `com.socialdatax/kuaishou-insights`
- Hosted MCP endpoint: `https://mcp.52choujiang.com/kuaishou/mcp`
- Hosted auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Default client transport: hosted `streamable-http`
- Command/stdio fallback: `npx -y mcp-remote https://mcp.52choujiang.com/kuaishou/mcp --header "Authorization: Bearer <SOCIALDATAX_API_KEY>"`
- License: MIT for the public documentation and examples only

## Safety Checks

- No real API keys are present.
- No private backend implementation is included.
- No production configuration is included.
- No internal samples are included.
- No account data or credentials are included.
- No generated build output is included.
- Public text uses neutral product wording.
- Public docs do not expose internal business code.

## Required Files

- `README.md`
- `LICENSE`
- `server-card.json`
- `mcp.json`
- `glama.json`
- `examples/streamable_http_config.json`
- `examples/claude_desktop_config.json`
- `examples/cursor_mcp.json`
- `examples/codex_config.toml`
- `assets/logo.png`

## Directory Checks

- Hosted streamable HTTP clients can connect directly to `https://mcp.52choujiang.com/kuaishou/mcp` with `Authorization: Bearer <SOCIALDATAX_API_KEY>`.
- With a valid key, hosted MCP `initialize` succeeds.
- With a valid key, hosted MCP `tools/list` returns the current 14 public tools.
- `kuaishou_get_hot_search_list` is present in `tools/list`; if it is missing, deploy the latest service before publishing.
- `kuaishou_submit_video_speech_text_by_video_url`, `kuaishou_submit_video_speech_text_by_photo_id`, and `kuaishou_get_video_speech_text_job` are present in `tools/list`; if any are missing, deploy the latest service before publishing.
- `examples/codex_config.toml` uses remote HTTP URL and `bearer_token_env_var`, not `mcp-remote`.
- `examples/cursor_mcp.json` uses remote HTTP URL and `headers` with `${env:SOCIALDATAX_API_KEY}`, not `mcp-remote`.
- `mcp.json` is explicitly command/stdio fallback and uses `mcp-remote`.
- Before submitting to directories, verify `https://mcp.52choujiang.com/kuaishou/.well-known/mcp/server-card.json` returns the Kuaishou server card, not the root XHS server card.

## Directory Submission Order

1. Official MCP Registry
2. GitHub public repository
3. Glama
4. ModelScope MCP 广场
5. MCP.Directory
6. MCP.so
7. mcpservers.org
8. MCP Market
9. Cline MCP Marketplace
10. awesome-mcp-servers / awesome-remote-mcp-servers

## Search Keywords To Verify After Approval

- `Kuaishou`
- `Kuaishou MCP`
- `Kuaishou data MCP`
- `Kuaishou hot list MCP`
- `Kuaishou comments MCP`
- `Kuaishou creator MCP`
- `Kwai`
- `Kwai MCP`
- `快手`
- `快手 MCP`
- `快手 数据 MCP`
- `快手 热榜 MCP`
- `快手 作品 MCP`
- `快手 评论 MCP`
- `快手 达人 MCP`
- `SocialDataX`
- `社媒数据助手`

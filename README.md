# Relier Mail connector for Claude

Relier Mail gives each of your projects its own email address. Send or forward email to a project, and Claude reads it with this connector. You use your own Claude subscription. The connector is read-only: Claude cannot send, change, or delete email, and cannot change your account.

This repository holds the public documentation of the connector and the Claude Code plugin that bundles it.

## Connect from claude.ai or Claude Desktop

1. Open **Settings → Connectors**.
2. Select **Add custom connector** and enter `https://mail-api.relier.ai/mcp`. When the connector is listed in the Claude Directory, enable **Relier Mail** there instead.
3. Sign in with your Relier Mail account in the page that opens, then select **Allow**.

## Connect from Claude Code

```sh
claude mcp add --transport http relier-mail https://mail-api.relier.ai/mcp
```

Then run `/mcp`, select `relier-mail`, and authenticate in the browser.

To install the plugin, which adds a skill that guides Claude through the tools:

```sh
claude plugin marketplace add d6u/relier-mail-claude-plugin
claude plugin install relier-mail
```

## What Claude can do

| Tool | Purpose |
| - | - |
| `list_projects` | Lists your projects with the email count and the newest arrival of each. |
| `list_emails` | Lists the email in one project, newest first, with a short snippet. Pages with a cursor. |
| `get_email` | Returns one email in full, with the extracted text of PDF attachments. |
| `search_emails` | Finds email by subject, sender, or body text, in one project or in all projects. |

Limits: lists return at most 50 rows per call. An email body is cut at 100,000 characters and marked as truncated. At most 20 attachments are returned, each with at most 20,000 characters of text.

## Requirements

* A Relier Mail account at <https://mail.relier.ai> with a verified email address. All plans, including Free, can connect.
* A Claude plan that supports connectors or Claude Code.

## Sign-in and data

* Sign-in uses OAuth 2.1 with PKCE. Claude registers itself with the Relier Mail authorization server and receives an access token for your account only.
* Access tokens are valid for 1 hour. Refresh tokens are valid for 30 days and rotate on each use.
* To disconnect, remove the connector in Claude. Relier Mail then stops accepting its tokens when they expire.
* Email text is third-party content. The connector returns it in fields named `untrustedContent`, `untrustedSnippet`, and `untrustedText`, and each tool tells Claude to treat it as data, not as instructions.
* Privacy policy: <https://relier.ai/privacy>. Terms: <https://relier.ai/terms>.

## Support

Email <support@relier.ai>.

## License

MIT. See [LICENSE](LICENSE).

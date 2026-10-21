# Wicle MCP for Cursor

Connect your AI assistant to your [Wicle](https://wicle.io/) project to explore website traffic and conversion trends, inspect funnels and segments, and manage analytics settings and dashboards.

This repository contains the Cursor plugin's connection configuration and documentation. The MCP service is hosted by Wicle; installing this plugin does not run a local server.

**Release status:** Initial distribution package. Marketplace submission and end-to-end validation of plugin installation, project configuration, and OAuth connection are pending.

## Requirements

- A Wicle account with membership in the organization that owns your project.
- A project with MCP enabled by an organization owner.
- A Cursor version that supports plugins with configurable variables and remote MCP connections.

The plugin has no separate fee. Your Wicle plan and the connected project's shared query limits apply.

## Configure the connection

1. Sign in to [Wicle](https://app.wicle.io/) and select the project you want to connect.
2. Open the project's settings and select **MCP**. Ask an organization owner to enable MCP if it is disabled.
3. Copy the project ID at the end of the displayed MCP URL: `https://app.wicle.io/mcp/projects/<project-id>`. The ID is a 24-character hexadecimal value. Do not enter the entire URL as the project ID.
4. In Cursor's plugin configuration, set **WICLE_PROJECT_ID** to that ID. Team administrators configure plugin variables in the Cursor dashboard under **Plugins → Configure**.
5. Complete the Wicle OAuth login when Cursor asks you to connect. Select **Read only** for analysis and configuration inspection, or **Full** when you need to create or change settings.
6. Ask the assistant: “Which Wicle project am I connected to, and what permissions does this connection have?” Verify the project and permissions before continuing.

Marketplace installation instructions will be added after the plugin is listed. Until then, the package is available for local evaluation using [Cursor's plugin documentation](https://cursor.com/docs/plugins).

If a `wicle` MCP connection already exists, check its project URL before adding another connection. Preserve existing connections to other projects and give an additional connection a different name.

## Example prompts

- “Compare sessions and conversions over the last seven days with the previous seven days. Explain the metric definitions and any data limitations.”
- “List the saved funnels and explain the steps in the funnel I select.”
- “Show the available segments and suggest which ones to compare when investigating a conversion drop.”
- “Inspect the event definitions and measurement settings before proposing an analysis.”

## Permissions and data

Read only connections expose read operations. Full connections can also expose operations that create, update, or delete settings, subject to your Wicle permissions. Review proposed changes and check the result after a write.

Wicle checks organization membership, the connected project, MCP enablement, and operation permissions. Selecting Full does not grant access to projects outside your organization.

Analysis results and any visitor data retrieved through MCP are sent to the connected AI service. Check your organization's requirements and the AI service's data settings before connecting. Access to visitor attributes is controlled separately in Wicle's MCP settings.

Keep passwords, access tokens, and reviewer credentials out of this repository and issue reports. This plugin uses OAuth and does not include a shared API key.

## Troubleshooting and support

- **Wrong project:** check the MCP URL in Wicle and the `WICLE_PROJECT_ID` plugin variable.
- **Access denied:** check that your account still belongs to the project's organization and that MCP is enabled.
- **Write tools unavailable:** verify that the connection was authorized with Full permissions and that your Wicle role allows the operation.
- **Query limit reached:** follow the retry information returned by Wicle. The limit is shared within the project.
- **Connection fails:** use the support channel available in your Wicle account and include the client name and a description of the problem without credentials or visitor data.

Public links: [Documentation](https://docs.wicle.io/), [Privacy policy](https://wicle.io/privacy-policy), [Terms of use](https://wicle.io/terms-of-use).

## License

The configuration and documentation in this repository are distributed under the [MIT License](LICENSE). The hosted Wicle service is governed by its own terms. Wicle and PLAID names and logos identify their respective brands.

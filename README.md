# Wicle MCP

Connect website analytics and AI-native A/B testing to your AI assistant. Analyze visitor behavior, uncover conversion bottlenecks, and design, implement, and evaluate A/B tests in your [Wicle](https://wicle.io/) project.

This repository contains connection documentation for Wicle's hosted MCP service and a Cursor plugin configuration. Supported MCP clients connect over HTTPS using OAuth; no local MCP server is required.

Directory listings are not yet confirmed. You can add the hosted MCP URL manually in clients that support custom remote connectors.

## Requirements

- A Wicle account with membership in the organization that owns your project.
- A project with MCP enabled by an organization owner.
- An MCP client that supports remote Streamable HTTP connections and OAuth. Your client plan and organization settings must allow custom connectors.

The plugin has no separate fee. Your Wicle plan and the connected project's shared query limits apply.

## Find your project's MCP URL

1. Sign in to [Wicle](https://app.wicle.io/) and select the project you want to connect.
2. Open the project's settings and select **MCP**. Ask an organization owner to enable MCP if it is disabled.
3. Copy the displayed MCP URL: `https://app.wicle.io/mcp/projects/<project-id>`. Use your own project's URL. The project ID is a 24-character hexadecimal value.

## Connect from Claude

1. Open Claude's connector settings and choose **Add custom connector**. You can also add a connector from the chat composer's connectors menu.
2. Enter a name such as **Wicle** and paste the full MCP URL copied from your Wicle project.
3. Choose **Sign in now**, **Use Claude's public identity** (CIMD), and **Streamable HTTP** if Claude asks for these settings. No client secret or custom request headers are required.
4. Add the connector and complete Wicle's OAuth consent. Choose **Read only** for analysis and configuration inspection, or **Full** to create, update, or delete settings and A/B test variations.
5. In a Claude conversation, enable the Wicle connector and ask: “Which Wicle project am I connected to, and what permissions does this connection have?” Check the project and permissions before continuing.

See [Claude's custom connector documentation](https://support.anthropic.com/en/articles/11175166-about-custom-integrations-using-remote-mcp) for client availability and organization controls.

## Connect from Cursor

1. Use a Cursor version that supports plugins with configurable variables and remote MCP connections.
2. In this plugin's configuration, set **WICLE_PROJECT_ID** to the project ID at the end of your MCP URL. Do not enter the entire URL as the variable value. Team administrators configure plugin variables in the Cursor dashboard under **Plugins → Configure**.
3. Complete Wicle's OAuth consent when Cursor asks you to connect. Choose **Read only** for analysis and configuration inspection, or **Full** to create or change settings.
4. Ask the assistant: “Which Wicle project am I connected to, and what permissions does this connection have?” Check the project and permissions before continuing.

Marketplace installation instructions will be added after the plugin is listed. Until then, the package is available for local evaluation using [Cursor's plugin documentation](https://cursor.com/docs/plugins).

If a `wicle` MCP connection already exists, check its project URL before adding another connection. Preserve existing connections to other projects and give an additional connection a different name.

## Example prompts

- “Compare sessions and conversions over the last seven days with the previous seven days. Explain the metric definitions and any data limitations.”
- “List the saved funnels and explain the steps in the funnel I select.”
- “Show the available segments and suggest which ones to compare when investigating a conversion drop.”
- “Inspect the event definitions and measurement settings before proposing an analysis.”
- “Help me design and implement an A/B test variation, and save it as a draft.” Saving changes requires Full access.

## Permissions and data

Read only connections expose read operations. Full connections can also expose operations that create, update, or delete settings, subject to your Wicle permissions. Review proposed changes and check the result after a write.

Wicle checks organization membership, the connected project, MCP enablement, and operation permissions. Selecting Full does not grant access to projects outside your organization.

Analysis results and any visitor data retrieved through MCP are sent to the connected AI service. Check your organization's requirements and the AI service's data settings before connecting. Access to visitor attributes is controlled separately in Wicle's MCP settings.

Keep passwords, access tokens, and reviewer credentials out of this repository and issue reports. These connections use OAuth and do not include a shared API key.

## Troubleshooting and support

- **Wrong project:** check the MCP URL in Wicle and your client. For the Cursor plugin, also check the `WICLE_PROJECT_ID` variable.
- **Access denied:** check that your account still belongs to the project's organization and that MCP is enabled.
- **Write tools unavailable:** verify that the connection was authorized with Full permissions and that your Wicle role allows the operation.
- **Query limit reached:** follow the retry information returned by Wicle. The limit is shared within the project.
- **Connection fails:** use the support channel available in your Wicle account and include the client name and a description of the problem without credentials or visitor data.

Public links: [Documentation](https://docs.wicle.io/), [Privacy policy](https://wicle.io/privacy-policy), [Terms of use](https://wicle.io/terms-of-use).

## License

The configuration and documentation in this repository are distributed under the [MIT License](LICENSE). The hosted Wicle service is governed by its own terms. Wicle and PLAID names and logos identify their respective brands.

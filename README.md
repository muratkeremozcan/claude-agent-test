# Claude Desktop Model Context Protocol (MCP) Setup Guide

1. Download Claude Desktop https://claude.ai/download, install, open

2. Open the Claude folder and create a file there `claude_desktop_config.json`. Open it.

   ```bash
   open ~/Library/Application\ Support/Claude
   touch ~/Library/Application\ Support/Claude/claude_desktop_config.json
   
   code ~/Library/Application\ Support/Claude/claude_desktop_config.json
   ```

3. Setup [Brave Search MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/brave-search) so that Claude can browse the web 

   > Model Context Protocol - *component that enhances the capability of model-based systems to understand and utilize context effectively. In applications like Brave Search, MCP ensures that search results are not only accurate but also highly relevant to the user's specific context, leading to a superior user experience.*

   Copy the npx setup to `claud_desktop_config.json`

   ```json
   {
     "mcpServers": {
       "brave-search": {
         "command": "npx",
         "args": [
           "-y",
           "@modelcontextprotocol/server-brave-search"
         ],
         "env": {
           "BRAVE_API_KEY": "YOUR_API_KEY_HERE"
         }
       }
     }
   }
   ```

   Get a Brave API Key

   1. Sign up for a [Brave Search API account](https://brave.com/search/api/)
   2. Choose a plan (Free tier available with 2,000 queries/month)
   3. Generate your API key [from the developer dashboard](https://api.search.brave.com/app/keys)

​	Restart Claude desktop and you should see MCP tools available 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9hrat7o2lpkv87pifnia.png)

4. Setup [GitHub MCP](https://github.com/modelcontextprotocol/servers/tree/main/src/github)

   [Create a GitHub Personal Access Token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens) with appropriate permissions:

   - Go to [Personal access tokens](https://github.com/settings/tokens) (in GitHub Settings > Developer settings)
   - Select which repositories you'd like this token to have access to (Public, All, or Select)
   - Create a token with the `repo` scope ("Full control of private repositories")
     - Alternatively, if working only with public repositories, select only the `public_repo` scope
   - Copy the generated token

Copy the npx setups to `claude_desktop_config.json`

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    }
  }
}
```

Close and open Claude. You should see more MCP tools.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1brqnk7jga03zohipzcx.png)

5. Test it all with a single prompt in Claude desktop

   ```
   Please do the following:
   
   - make a simple html page
   - create a repository called "claude-agent-test"
   - push the html page to the "claude-agent-test" repo
   - add a little css to the html page and push it up
   - make an issue suggesting we add some more context to the html page
   - now make a branch called feat/test-claude-mcp, make that fix and push the change
   - make a pull request against main with these changes
   ```

   

## Note
Replace `YOUR_API_KEY_HERE` and `YOUR_GITHUB_TOKEN` with your actual credentials.

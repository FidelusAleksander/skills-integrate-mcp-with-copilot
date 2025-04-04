## Step 2: Using Copilot Agent Mode with GitHub MCP Server

You have just connected a first external MCP server to Copilot Chat!

GitHub MCP Server exposes multiple tools for Copilot to use. Examples include searching GitHub, managing repositories, issues, pull requests and much more.

You interact with Copilot in natural language, and Copilot determines if what you are asking for is something that can be done through any MCP Servers you have currently running in your environment. Isn't that cool?

> [!NOTE]
> The GitHub MCP Server is limited to operations permitted by the `GITHUB_TOKEN` scope in your `.vscode/mcp.json` configuration.

### :keyboard: Activity: Use Copilot for issue resolution

In the background your repository just received a [bug report]({{{bug_report_url}}}) issue from one of the Mergington High School students trying to access the website.

Let's use GitHub Copilot Agent Mode together with GitHub MCP server to work on that issue.

1. Open the **Copilot Chat Agent Mode** panel in VS Code, click the 🛠️ Tools icon and ensure that GitHub MCP Server is running and the tools are enabled

   <details>
   <summary>:camera_flash: See screenshot</summary><br/>

   ![image](https://github.com/user-attachments/assets/6a6740ae-f7a6-40dc-870a-8c9869faabd7)


   </details>

1. Ask Copilot if there are any open bug reports on your repository:

   > <img width="13px" src="https://github.com/user-attachments/assets/98fd5d2e-ea29-4a4a-9212-c7050e177a69" /> **Prompt**
   >
   > ```prompt
   > Are there any open bug report issues on my repository ({{{full_repo_name}}}) ?
   > ```

   <details>
   <summary>:camera_flash: Copilot should figure out that it can use GitHub MCP server for this. </summary><br/>

   <img width="400px" src="https://github.com/user-attachments/assets/7a9aea70-7c50-46d8-848e-092ade825573" />

   </details>
   
   
   


   > 🪧 **Note:** We explicitly include the repository name to add it to Copilot's session context. For subsequent prompts, this context will be preserved in the conversation.

   > ✨ **Bonus:** You are welcome to try the prompt without it and if Copilot chooses to list issues in a different repository, guide it your way.

1. Once Copilot identifies a bug report, ask it to implement a fix in your codebase:

   > <img width="13px" src="https://github.com/user-attachments/assets/98fd5d2e-ea29-4a4a-9212-c7050e177a69" /> **Prompt**
   >
   > ```prompt
   > #codebase Okay, let's start working on the bug report.
   > Comment on the issue that I will take a look at the issue and try to fix it.
   > Introduce the changes to the activities, push the changes to a new branch, and raise a pull request to `main`.
   > ```

   > ⚠️ **Warning:** Always verify the information that Copilot passes to the MCP server before accepting.

1. Follow Copilot's guidance to create a pull request with the fix.

   > 🪧 **Note:** Remember that Copilot is conversational, and you are power of guiding the AI assistant to implement what's on your mind.

1. Once the pull request is created, Mona will start checking your work. Give her a moment and keep watch of the comments. You will see her respond with progress info and the next step!

<details>
<summary>Having trouble?</summary><br/>

If you encounter issues:

- Make sure your MCP configuration is properly set up from Step 1
- Verify that the tools are executed on your repository ({{{full_repo_name}}}). Whenever a MCP tool is invoked you can inspect what Copilot passes to the MCP Server.

</details>

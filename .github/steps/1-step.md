## Step 1: Introduction to MCP and environment setup

In this exercise, you'll learn how to use Model Context Protocol (MCP) to connect GitHub Copilot to your entire toolchain.
This integration allows you to solve problems across platforms without leaving your code editor. **Less context switching, more coding**.

### What is Model Context Protocol (MCP)?

[Model Context Protocol (MCP)](https://modelcontextprotocol.io/introduction) is often referred to as "USB-C for AI" - a universal connector that allows GitHub Copilot to seamlessly interact with external tooling.

```mermaid
graph LR
    A[Developer] -->|Uses| B[GitHub Copilot]
    B -->|Unified API| MCP[Model Context Protocol]

    MCP <-->|Unique API| C[(GitHub)]
    MCP <-->|Unique API| D[(Slack)]
    MCP <-->|Unique API| E[(Figma)]

    style B fill:#4CAF50,stroke:#333,stroke-width:2px

    subgraph "Less Context Switching, More Coding"
        B
        MCP
        C
        D
        E

    end
```

### :keyboard: Activity: Get to know your environment

Let's start up our development environment and familiarize with the environment.

We are using the same web application as in the [Getting Started with Copilot](https://github.com/skills/getting-started-with-github-copilot) exercise - the Mergington High School's extracurricular activities website.

1. Right-click the below button to open the **Create Codespace** page in a new tab. Use the default configuration.

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)

1. Validate the Copilot Chat and Python extensions are installed and enabled
   <details>
   <summary>:camera_flash: See screenshot</summary><br/>

   <img width="350" alt="copilot extension for VS Code" src="https://github.com/user-attachments/assets/ef1ef984-17fc-4b20-a9a6-65a866def468" />

   <img width="350" alt="python extension for VS Code" src="https://github.com/user-attachments/assets/3040c0f5-1658-47e2-a439-20504a384f77" />
   </details>

1. In the left sidebar, select the `Run and Debug` tab and then press the **Start Debugging** icon.

   <details>
   <summary>:camera_flash: See screenshot</summary><br/>

   <img width="300" alt="run and debug" src="https://github.com/user-attachments/assets/50b27f2a-5eab-4827-9343-ab5bce62357e" />

   </details>

1. Throughout the exercise, you can access the website link from the `ports` tab on port `8000`.

   <details>
   <summary>:camera_flash: See screenshot</summary><br/>
       
    <img width="200" alt="ports tab" src="https://github.com/user-attachments/assets/bd25ed3c-0656-448c-b809-edc10c0ab6cf" />


   </details>

### :keyboard: Activity: Set up a MCP server for your project

1. Inside your codespace, create a new file named `mcp.json` in the `.vscode` directory and paste the following contents:

   ```json
   // .vscode/mcp.json
   {
     "servers": {
       "github": {
         "command": "npx",
         "args": ["-y", "@modelcontextprotocol/server-github"],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "${input:githubToken}"
         }
       }
     },
     "inputs": [
       {
         "type": "promptString",
         "id": "githubToken",
         "description": "Enter your GitHub personal access token",
         "password": true
       }
     ]
   }
   ```

1. In a moment, when you start the server - you will be prompted to provide a GitHub Token. Print it out in the terminal and copy it to your clipboard (`CTRL+C`).

   ```bash
      echo $GITHUB_TOKEN
   ```

1. Back in the `.vscode/mcp.json` file you should see `Start` button show up like so:

   ![image](https://github.com/user-attachments/assets/c82a4202-1f4a-4123-ad14-5e33ecd6316c)

1. Click the `Start` button to launch the GitHub MCP server locally. When prompted, paste the GitHub token you copied earlier.

1. Validate the server is running.

   1. The `.vscode/mcp.json` file should show if the server you started is running

      <details>
      <summary>:camera_flash: See screenshot</summary><br/>

      ![image](https://github.com/user-attachments/assets/80f3fcda-34a8-486e-95a3-c166e9152b9a)

      </details>

   1. You should see additional tools available in Copilot Agent Mode

      <details>
      <summary>:camera_flash: See screenshot</summary><br/>

      ![image](https://github.com/user-attachments/assets/95af044c-3f26-4f5c-b933-7630db72eb67)

      </details>

   1. You can use the VSCode command palette `Ctrl+Shift+P` or `Command+Shift+P` on Mac.
      Start typing `> MCP` to see different MCP commands, such as listing active servers.

         <details>
         <summary>:camera_flash: See screenshot</summary><br/>

      ![image](https://github.com/user-attachments/assets/6a127ac2-a6dc-495b-bc5f-d52425f709f8)

         </details>

1. Commit and push the `.vscode/mcp.json` file to the `main` branch

<details>
<summary>Having trouble?</summary><br/>

Make sure you:

- Properly copied the `json` contents above to `.vscode/mcp.json` file
- Pushed your changes to the `main` branch

</details>

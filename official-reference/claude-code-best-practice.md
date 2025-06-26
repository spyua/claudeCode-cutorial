This document outlines best practices for using Claude Code, a command-line tool for agentic coding. It is designed to be read and understood by an AI, providing a structured overview of effective techniques for leveraging the tool across various development tasks.

### **1. Customize Your Setup**

Optimizing Claude Code begins with tailoring its environment to your specific project needs. This reduces token consumption and streamlines context gathering.

#### **a. Create `CLAUDE.md` Files**

The `CLAUDE.md` file is a special Markdown file that Claude automatically ingests for context at the start of a session. This file is ideal for project-specific instructions and guidelines.

**Recommended Content for `CLAUDE.md`:**

  * **Common Commands:** Document frequently used shell commands.
  * **Core Files:** List essential files and utility functions.
  * **Style Guides:** Specify coding style preferences (e.g., module syntax, import patterns).
  * **Testing Instructions:** Detail how to run tests, including performance considerations.
  * **Repository Etiquette:** Define standards for branching, merging, and other version control practices.
  * **Environment Setup:** Note requirements like compiler versions or environment management tools.
  * **Project Quirks:** Mention any unusual behaviors or warnings specific to the repository.

**Example `CLAUDE.md`:**

```markdown
# Bash commands
- npm run build: Build the project
- npm run typecheck: Run the typechecker

# Code style
- Use ES modules (import/export) syntax, not CommonJS (require)
- Destructure imports when possible (eg. import { foo } from 'bar')

# Workflow
- Be sure to typecheck when you’re done making a series of code changes
- Prefer running single tests, and not the whole test suite, for performance
```

**Locations for `CLAUDE.md`:**

  * **Repository Root:** The most common location, checked into version control for team-wide use.
  * **Parent Directories:** Useful in monorepos to provide cascading context.
  * **Child Directories:** Provides context on-demand when working within subdirectories.
  * **Home Folder (`~/.claude/CLAUDE.md`):** For global settings across all sessions.

The `/init` command can be used to automatically generate a `CLAUDE.md` file.

#### **b. Tune Your `CLAUDE.md` Files**

Treat `CLAUDE.md` files as prompts that require refinement. Avoid adding excessive content without testing its impact on the model's performance. Use the `#` key during a session to give Claude an instruction that it will automatically add to the relevant `CLAUDE.md` file. For emphasis, use keywords like "IMPORTANT" or "YOU MUST".

#### **c. Curate Allowed Tools**

By default, Claude Code prioritizes safety by requiring permission for actions that modify the system. You can customize the allowlist for tools you deem safe.

**Methods for Managing Allowed Tools:**

1.  **"Always allow"**: Select this option when prompted during a session.
2.  **`/permissions` Command**: Add or remove tools from the allowlist.
      * Example: `Edit` to always allow file edits.
      * Example: `Bash(git commit:*)` to allow all git commit commands.
3.  **Manual Edit**: Modify `.claude/settings.json` or `~/.claude.json`.
4.  **CLI Flag**: Use `--allowedTools` for session-specific permissions.

#### **d. Install the `gh` CLI**

If you use GitHub, installing the `gh` command-line interface allows Claude to interact with GitHub for managing issues, pull requests, and more.

### **2. Give Claude More Tools**

Extend Claude's capabilities by providing it with access to custom scripts, APIs, and more complex tools.

#### **a. Bash Tools**\</h4\>

Claude can use any tool in your shell environment. To enable it to use custom tools, provide instructions by:

  * Telling it the tool name and showing usage examples.
  * Instructing it to run the `--help` flag for documentation.
  * Documenting the tool in your `CLAUDE.md` file.

#### **b. MCP (Machine-Claude Protocol)**\</h4\>

Claude Code can act as an MCP client, connecting to MCP servers to access additional tools. Configure MCP connections in your project, global configuration, or a `.mcp.json` file. Use the `--mcp-debug` flag for troubleshooting.

#### **c. Custom Slash Commands**\</h4\>

Store prompt templates for repeated workflows in Markdown files within the `.claude/commands` folder. These become accessible as slash commands. Use the `$ARGUMENTS` keyword to pass parameters.

**Example Custom Slash Command (`.claude/commands/fix-github-issue.md`):**

```markdown
Please analyze and fix the GitHub issue: $ARGUMENTS.

Follow these steps:

1. Use `gh issue view` to get the issue details
2. Understand the problem described in the issue
3. Search the codebase for relevant files
4. Implement the necessary changes to fix the issue
5. Write and run tests to verify the fix
6. Ensure code passes linting and type checking
7. Create a descriptive commit message
8. Push and create a PR

Remember to use the GitHub CLI (`gh`) for all GitHub-related tasks.
```

This would be invoked as `/project:fix-github-issue 1234`.

### **3. Common Workflows**

While Claude Code is flexible, several effective patterns have emerged.

  * **Explore, Plan, Code, Commit:**

    1.  **Explore:** Ask Claude to read relevant files or URLs without writing code.
    2.  **Plan:** Instruct Claude to create a plan. Use phrases like "think" or "think hard" to allocate more computation time for planning.
    3.  **Code:** Ask Claude to implement the planned solution.
    4.  **Commit:** Have Claude commit the result and create a pull request.

  * **Test-Driven Development (TDD):**

    1.  Ask Claude to write tests based on expected inputs and outputs.
    2.  Confirm that the tests fail.
    3.  Commit the failing tests.
    4.  Instruct Claude to write code that passes the tests, iterating until all tests succeed.
    5.  Commit the implementation code.

  * **Visual Iteration:**

    1.  Provide Claude a way to see its output (e.g., via a Puppeteer MCP server for screenshots).
    2.  Give Claude a visual mock-up (e.g., an image file or pasted screenshot).
    3.  Ask Claude to implement the design, take screenshots, and iterate until the output matches the mock.
    4.  Commit the final result.

  * **Codebase Q\&A:**
    Use Claude to learn a new codebase by asking questions you would ask a human colleague. Claude will agentically search the code to find answers.

      * *Example Question:* "How does logging work in this project?"
      * *Example Question:* "What does `async move { ... }` do on line 134 of `foo.rs`?"

  * **Git and GitHub Interaction:**
    Use Claude for a majority of `git` and `gh` interactions, such as searching history, writing commit messages, resolving conflicts, creating pull requests, and fixing build failures.

  * **Jupyter Notebooks:**
    Claude can read, write, and interpret Jupyter notebooks, including their outputs and images, to assist with data exploration and analysis.

### **4. Optimize Your Workflow**

Apply these general principles to enhance your effectiveness with Claude Code.

  * **Be Specific:** Provide clear, detailed instructions to improve the success rate on the first attempt.
  * **Give Claude Images:** Use images and diagrams for context, especially for UI development and data visualization.
  * **Mention Files:** Use tab-completion to reference specific files and folders.
  * **Give Claude URLs:** Paste URLs for Claude to fetch and read.
  * **Course Correct:** Be an active collaborator. Use `Escape` to interrupt Claude, `double-Escape` to edit a previous prompt, and ask Claude to `undo` changes.
  * **Use `/clear`:** Reset the context window between tasks to maintain focus and performance.
  * **Use Checklists:** For complex tasks, have Claude use a Markdown file as a checklist or scratchpad to track progress.

### **5. Use Headless Mode to Automate Infrastructure**

Claude Code's headless mode is for non-interactive use in CI/CD, scripts, and other automations.

  * **Enable Headless Mode:** Use the `-p` flag followed by a prompt.
  * **Example Use Case (Issue Triage):** Automate the labeling of new GitHub issues.
  * **Example Use Case (Linter):** Use Claude to perform subjective code reviews, identifying issues like typos or misleading variable names.

### **6. Uplevel with Multi-Claude Workflows**

Run multiple instances of Claude in parallel for more complex tasks.

  * **Separate Verification:** Use one Claude instance to write code and a second, separate instance to review or test it. This separation of context often yields better results.
  * **Multiple Checkouts/Worktrees:** For independent tasks, create multiple `git` checkouts or lighter-weight `git worktrees`. This allows you to run multiple Claude sessions simultaneously on different branches without conflict.
  * **Custom Harness with Headless Mode:**
      * **Fanning Out:** For large migrations, have Claude generate a task list, then loop through the list, calling `claude -p` programmatically for each item.
      * **Pipelining:** Integrate Claude into data processing pipelines by piping its output to other commands (e.g., `claude -p "<prompt>" --json | your_next_command`).
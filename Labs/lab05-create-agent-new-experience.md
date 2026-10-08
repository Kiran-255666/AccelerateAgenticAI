---
lab:
  title: Create an agent using the new Copilot Studio experience
  module: Create agents in Microsoft Copilot Studio
  description: In this lab, you will use the new Copilot Studio experience to create an instruction-driven agent, add a prebuilt action, and test autonomous reasoning behavior.
  duration: 30 minutes
  level: 200
  islab: true
  primarytopics:
    - Microsoft Copilot Studio
---

# Create an agent using the new Copilot Studio experience

## Scenario

In this exercise, you will:

- Switch to the new Copilot Studio experience
- Create an agent using natural language instructions
- Add a prebuilt action the agent can use autonomously
- Test the agent and observe its reasoning behavior
- Refine instructions based on test results

This exercise will take approximately **30** minutes to complete.

## What you will learn

- How the new Copilot Studio experience differs from the classic interface
- How to configure an agent using instructions instead of topic trees
- How the agent reasons autonomously to select knowledge and actions
- How to iterate on instructions to improve agent behavior

## High-level lab steps

- Switch to the new Copilot Studio experience
- Create an agent with a description
- Write and refine agent instructions
- Add a prebuilt action
- Test and iterate

## Prerequisites

- Have a Microsoft Entra ID account
- Have a Copilot Studio license or have signed up for a free trial
- Have access to a Power Platform environment and a solution where you can create agents and related assets.
- You can use:
  - the environment and **Lab Exercises** solution created in the **ILT Setup** lab, or
  - your own existing environment and solution.
- If you do not already have an environment and solution prepared, complete the steps in the **ILT Setup** lab before continuing.

> [!IMPORTANT]
> The new Copilot Studio experience is the redesigned interface that replaces the classic topic authoring canvas. Steps and screenshots in this lab reflect the new experience. If your environment shows the classic interface, follow the prompt to switch to the new experience before proceeding.

## Key concept: Instruction-driven agents

The new Copilot Studio experience replaces the topic authoring canvas with a simpler, instruction-driven model:

| Classic experience | New experience |
|---|---|
| Agent behavior defined by topic trees and trigger phrases | Agent behavior defined by natural language instructions |
| Author builds explicit conversation flows node by node | Agent reasons dynamically about how to respond |
| Topics, conditions, and branches control conversation routing | Instructions, knowledge, and actions determine what the agent does |
| Actions require building a Power Automate workflow, configuring inputs/outputs, and adding it as a tool | Prebuilt connector actions are added directly in Copilot Studio — no workflow authoring required |

The new experience is best suited for agents that need to handle open-ended, context-dependent conversations. The classic experience (covered in later labs) remains the right choice when you need a guaranteed, auditable sequence of steps — for example, collecting structured data in a specific order.

## Exercise 1 - Switch to the new Copilot Studio experience

### Task 1.1 – Open the new experience

1. Navigate to the **Copilot Studio** new experience home page at `https://copilotstudio.preview.microsoft.com/`. If you are signed out or have not signed in, sign in using the credentials provided for the lab.

1. At the bottom of the left-hand navigation, select the current **environment name**, then select **All environments**. Select the **environment you created earlier for this exercise**.

   ![Safe Travels template.](../media/Testuser.png)

### Task 1.2 – Review the New Interface

Take a moment to review how the new Copilot Studio experience is organized before creating your agent.
   
   ![New Interface](../media/uiuiui.png)

| Location | Name | Purpose |
|----------|------|---------|
| Left navigation | Home | Provides access to the Copilot Studio home page where you can create agents and workflows. |
| Left navigation | Operate | Used to monitor and manage agent operations and activity. |
| Left navigation | Chat | Allows you to interact with and test agents through conversations. |
| Left navigation | Agents | Displays existing agents and allows you to create and manage new agents. |
| Left navigation | Workflows | Used to create and manage automated workflows and business processes. |
| Home page | Agent | Creates an AI agent that can answer questions, follow instructions, use knowledge sources, and perform actions. |
| Home page | AI Workflow | Creates an AI-powered workflow that automates multi-step tasks using triggers and actions. |
| Home page | Other ways to build | Provides additional options for building agents and automation solutions. |

> **Note:** In the new Copilot Studio experience, agent behaviour is configured through **Instructions**, **Knowledge**, and **Actions**. The traditional **Topics** authoring experience is no longer available in the left navigation.

## Exercise 2 - Create an agent

In this exercise, you will create an IT support agent for a fictional company called **Contoso**. The agent will help employees troubleshoot common IT issues and submit support tickets.

### Task 2.1 – Create the agent


### Task 2.2 – Review and refine the auto-generated instructions

1. On the agent's **Build** tab, locate the **Instructions** section.

1. Review the instructions that were generated from your description. They should describe the agent's purpose, tone, and general behavior.

1. In the **Instructions** section, update the instructions by adding the following guidelines, then select **Save**:

   ```prompt
   ## Guidelines
   - Always respond in a professional and friendly tone.
   - For password reset requests, direct the employee to the self-service portal at https://aka.ms/sspr before offering to raise a ticket.
   - For issues you cannot resolve, collect the employee's name, email address, and a brief description of the issue before submitting a ticket.
   - Do not speculate about hardware failures. Always recommend contacting the IT desk directly for physical hardware issues.
   - When an employee's issue cannot be resolved, use the Send an email action to notify the IT helpdesk at helpdesk@contoso.com with the employee's name, email, and issue description.
   ```
   
   > [!NOTE]
   > Instructions in the new experience are the primary way to control agent behavior. Well-written instructions reduce the need for additional configuration and make the agent more predictable.

## Exercise 3 - Test and refine

In this exercise, you will test the agent and observe how it reasons before responding.

### Task 3.1 – Open the Preview tab

1. Select the **Preview** tab at the top of the page to test the agent.

1. When you test the agent, a reasoning summary appears automatically above each response, describing how the agent decided what to do. Select **Show more** on that summary to expand the full reasoning trace.

   > [!NOTE]
   > The reasoning trace is a key feature of the new experience. It shows which knowledge sources or actions the agent considered and why — for example, a **Loaded Skill** entry indicates which action or skill the agent invoked.

### Task 3.2 – Test the instructions

1. At the top of the **Preview** tab, select **New chat**.

1. Enter the following prompt:

   ```prompt
   I forgot my password and cannot log in.
   ```

   Based on the instructions you wrote, the agent should direct you to the self-service portal before offering to raise a ticket.

### Task 3.3 – Test the agent's reasoning behavior

1. At the top of the **Preview** tab, select **New chat**.

1. Enter the following prompt:

   ```prompt
   My laptop will not turn on at all.
   ```

   Based on the instructions you wrote, the agent should decline to troubleshoot the hardware failure remotely, recommend contacting the IT desk directly. The agent might also offer to submit a support ticket on your behalf.

1. If prompted, provide your name, email, and a brief description of the issue.

### Task 3.4 – Refine instructions based on test results

1. Review how the agent responded across the three test sessions.

1. If any response was not aligned with the intended behavior, select the **Build** tab, and in the **Instructions** section, adjust the relevant guideline.

   For example, if the agent did not mention the self-service portal for password resets, make the instruction more explicit:

   ```prompt
   - For ALL password-related requests, always mention https://aka.ms/sspr as the first step before any other assistance.
   ```

1. Select **Publish**, then select **Publish agent**. Once the agent is published, select **Done** and re-test the affected scenario.

> [!NOTE]
> Iterating on instructions is the primary tuning mechanism in the new experience. Small changes in wording can significantly change agent behavior.

## Summary

In this lab, you used the new Copilot Studio experience to create an instruction-driven IT support agent. You configured behavior entirely through natural language instructions and added a prebuilt connector action directly in Copilot Studio — without building a Power Automate workflow or leaving the page. Compared to Lab 03, where adding a tool required authoring a workflow, configuring inputs and outputs, and publishing it separately, the new experience significantly reduces the authoring effort for straightforward actions. You also used the reasoning trace in the Preview pane to observe how the agent decided what to do before generating a response. Having worked with both the classic and new experiences, you can now choose the right approach for each scenario: instruction-driven for open-ended conversations, and classic topics and workflows when you need a guaranteed, auditable sequence of steps.

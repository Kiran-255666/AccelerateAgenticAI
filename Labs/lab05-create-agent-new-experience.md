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

The new experience is best suited for agents that need to handle open-ended, context-dependent conversations. The classic experience, covered in later labs, remains the right choice when you need a guaranteed, auditable sequence of steps, for example, collecting structured data in a specific order.

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

1. In the left navigation, select **Agents**.

2. Select the **New Agent** dropdown, then select **Agent**.

3. Under **Other ways to build**, select **Agent (standard)**.

   ![Select Agent (standard).](../media/select-standard-agent.png)

4. On the **Name your agent** page, enter the following name:

   ```text
   Contoso IT Helpdesk
   ```

   ![Enter the agent name.](../media/enter-agent-name.png)

5. Under **Agent settings (Optional)**, review the available settings.

6. For **Language**, keep the default value **English (United States)**.

7. For **Solution**, select **labsolution**.

8. Review the **Schema name**. The schema name is generated automatically. Keep the generated value.

   ![Configure agent settings.](../media/configure-agent-settings.png)

9. Select **Create** to create the agent.

10. Wait for Copilot Studio to create the agent.

### Task 2.2 – Review and refine the auto-generated instructions

1. In the agent workspace, locate the **Instructions** section.

2. Review the instructions generated for the agent. They should describe the agent's purpose, tone, and general behavior.

3. In the **Instructions** section, add the following guidelines, then save the changes:

   ```prompt
   ## Guidelines

   - Always respond in a professional and friendly tone.

   - For password reset requests, direct the employee to the self-service portal at https://aka.ms/sspr before offering to raise a ticket.

   - For issues you cannot resolve, collect the employee's name, email address, and a brief description of the issue before submitting a ticket.

   - Do not speculate about hardware failures. Always recommend contacting the IT desk directly for physical hardware issues.

   - When an employee's issue cannot be resolved, use the Send an email action to notify the IT helpdesk at helpdesk@contoso.com with the employee's name, email, and issue description.
   ```

   ![Configure the agent instructions.](../media/configure-agent-instructions.png)

> [!NOTE]
> Instructions are the primary way to define agent behavior. Clear and specific instructions help the agent respond consistently to different user requests.

## Exercise 3 - Test and refine

In this exercise, you will test the agent with different IT support scenarios and refine its instructions based on the results.

### Task 3.1 – Open the test experience

1. Open the **Test** or **Preview** experience for the agent.

2. If an existing conversation is displayed, start a new chat.

   ![Open the agent test experience.](../media/open-agent-test.png)

> [!NOTE]
> The test experience allows you to interact with the agent and verify whether it follows the instructions you configured.

### Task 3.2 – Test the password reset scenario

1. Start a new chat.

2. Enter the following prompt:

   ```prompt
   I forgot my password and cannot log in.
   ```

3. Review the agent's response.

4. Verify that the agent directs you to the self-service password reset portal:

   ```text
   https://aka.ms/sspr
   ```

5. Confirm that the self-service portal is mentioned before the agent offers to raise a support ticket.

   ![Test the password reset scenario.](../media/test-password-reset.png)

> [!NOTE]
> If the agent does not mention the self-service portal first, refine the password reset instruction before continuing.

### Task 3.3 – Test the hardware issue scenario

1. Start a new chat.

2. Enter the following prompt:

   ```prompt
   My laptop will not turn on at all.
   ```

3. Review the agent's response.

4. Verify that the agent does not speculate about the cause of the hardware failure.

5. Verify that the agent recommends contacting the IT desk directly for the physical hardware issue.

6. If the agent offers to submit a support request, provide your name, email address, and a brief description of the issue.

   For example:

   ```text
   Name: Test User
   Email: test.user@contoso.com
   Issue: My laptop will not turn on at all.
   ```

7. Review the agent's response and verify that it handles the support request using the information provided.

   ![Test the hardware issue scenario.](../media/test-hardware-issue.png)

### Task 3.4 – Refine instructions based on test results

1. Review the agent's responses from the test scenarios.

2. If a response does not align with the intended behavior, return to the **Instructions** section and update the relevant guideline.

3. For example, if the agent did not mention the self-service portal first for a password reset request, make the instruction more explicit:

   ```prompt
   - For all password-related requests, always mention https://aka.ms/sspr as the first step before providing any other assistance.
   ```

4. Save the updated instructions.

5. Return to the test experience and start a new chat.

6. Re-test the scenario that did not produce the expected result.

7. Continue refining the instructions and testing the agent until its responses align with the intended behavior.

   ![Refine the agent instructions.](../media/refine-agent-instructions.png)

> [!NOTE]
> Iterating on instructions is an important way to improve agent behavior. Small changes in wording can affect how the agent responds to different requests.

## Summary

In this lab, you created a standard agent in the new Copilot Studio experience and configured its behavior using natural language instructions. You created an IT support agent for Contoso, added guidelines for handling password resets and hardware issues, and tested the agent with different user scenarios.

You also refined the instructions based on the agent's responses. This iterative approach helps improve agent behavior without requiring you to define every possible conversation path manually.

The new Copilot Studio experience is useful for agents that handle open-ended requests using instructions, knowledge, and actions. When a scenario requires a fixed and predictable sequence of steps, the classic topic-based approach can still be more appropriate.
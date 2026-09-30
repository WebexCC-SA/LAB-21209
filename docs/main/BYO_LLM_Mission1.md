---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 2: Register the LLM as an Agentic App

**<details><summary>What is an Agentic App? <span style="color: orange;"></span></summary>**

An Agentic App registers an external capability — in this case your own LLM — in the Webex ecosystem so administrators can approve it, configure authentication, and use it with Webex AI Agent.

## </details>

## Mission overview

Your mission is to:

**Register your LLM as an agentic app** in the **Webex Developer Portal**. This agentic app represents the preconfigured **OpenRouter GPT6-Luna** gateway from Mission 1.

---

## Build

### Task 1. Create an Agentic App in the Webex Developer Portal

1. Open the [Webex Developer Portal](https://developer.webex.com/){:target="_blank"}.

2. Click **Login**. Sign in with your admin credentials.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_8.png)

3. Under the profile menu, click **My Webex Apps**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_9.png)

4. Click **Create a New App**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_10.png)

5. On the next page, select **Create an Agentic App**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_11.png)

6. Under **Agentic App Module**, select **LLM Engine**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_12.png)

7. Enter the OpenRouter base URL that you found in Mission 1: **<copy>https://openrouter.ai/api/v1/chat/completions</copy>**
![Profiles](../graphics/Lab1_AI_Agent/OpenR_13.png)

8. For the LLM Service, select **Chat Completion V1**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_14.png)

9. Name your app **<copy><w class="attendee"></w>\_21209_CustomLLM</copy>**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_15.png)

10. For **Agent App Description**, paste the text below (use the **copy** icon on the code block):

    ``` text
    Custom LLM for Webex Event Health. This agentic app exposes an external Large Language Model that will be used as a Custom AI Engine for the Event Health autonomous AI agent.
    ```

11. Select an available Agentic App icon.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_16.png)

12. For **Agentic App auth type**, select **API key**, then click **Add Agentic App**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_17.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>

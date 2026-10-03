---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 4: Create and Assign the Custom AI Engine

**<details><summary>What is a Custom AI Engine? <span style="color: orange;"></span></summary>**

A Custom AI Engine lets Webex AI Agent use your own LLM for reasoning and generation, while Webex continues to manage media, state, orchestration, and channel integration.

## </details>

## Mission overview

Your mission is to:

**Create the AI Engine in AI Agent Studio**, point it at the agentic app you registered in Mission 2, and **assign it** to your Event Health AI agent. The engine uses the preconfigured **OpenRouter** gateway to reach **GPT6-Luna**.

---

## Build

### Task 1. Create the AI Engine

1. Go to [Control Hub](https://admin.webex.com){:target="_blank"}.

2. Open **Contact Center** from the left navigation, and under **Overview > Quick Links**, click **Webex AI Agent**.

3. In **AI Agent Studio**, open **AI Engines**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_22.png)

4. Click **Create AI Engine**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_23.png)

5. Provide the following information, then click **Next**.

    > Engine Name: **<copy><w class="attendee"></w>\_21209_CustomAIEngine</copy>**
    >
    > Description: **<copy>Custom Engine</copy>**
![Profiles](../graphics/Lab1_AI_Agent/OpenR_24.png)

6. Don't make any changes on the next page. Just click **Next**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_25.png)

7. Select your custom LLM that is related to your ID from the list. Search for **<copy><w class="attendee"></w>\_21209_CustomLLM</copy>**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_26.png)

8. In **Model name**, provide the exact LLM name that you saw in OpenRouter. Please review Mission 1, step 8. In this lab it is **<copy>openai/gpt-6-luna</copy>**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_27.png)

9. Select **Absent** for **Temperature** and **Top P**, because not all third-party models support these features.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_28.png)

10. Review the prompts for the model. This prompt will be appended to the instructions of your AI agent. You don't need to customize it in this lab, but for your business you can customize it for your needs. Then click **Next**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_29.png)

11. On the next page, click **Validate**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_30.png)

12. After validation is completed, click **Create engine**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_31.png)


### Task 2. Assign the engine to your existing agent

1. In **AI Agent Studio**, open **AI Agents**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_32.png)

2. Select the agent **<copy><w class="attendee"></w>\_21209_AutoAI_Lab</copy>**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_33.png)

3. In the agent profile, change **AI engine** from **Webex AI Pro-US 2.0** to **<copy><w class="attendee"></w>\_21209_CustomAIEngine</copy>**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_34.png)

4. Click **Save changes**.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_35.png)

5. **Publish** the AI agent. Provide a version name (for example, **V2-BYOLLM**).
![Profiles](../graphics/Lab1_AI_Agent/OpenR_36.png)

### Task 3. Test the Custom AI Engine

1. Click **Preview** and start a chat.

2. Send **<copy>I have a headache and need some help</copy>**. Confirm that the agent still answers using your Event Health knowledge and that responses are now driven by your Custom AI Engine.
![Profiles](../graphics/Lab1_AI_Agent/OpenR_37.png)

3. Call the phone number that is related to your Entry Point. Talk to the AI agent and try to order OTC medication with delivery. It uses the same AI Agent configuration, but a different LLM for chat completion on the backend. 

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>

---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 3: Configure Fulfillment Action and create a medication order using **Voice Flow**.

**<details><summary>What is a Fulfillment Action? <span style="color: orange;"></span></summary>**

Fulfillment Action is a task that an AI agent performs by understanding user intents and completing by connecting to external systems over an API.


## </details>

## Mission overview

In this Mission you will be using the Voice flow to execute the API call to create the medication order with a third party system.

![Profiles](../graphics/Lab1_AI_Agent/Fulfilment.png)

---

## Build

### Task 1. Configure Action in the AI Studio

1. Go to **Webex AI Agent Studio** Portal.

2. Select your AI agent with name **<copy><w class="attendee"></w>\_21209_AutoAI_Lab</copy>** that you created earlier and go to **Actions**. You will see one Action has already been created by default for the Agent Handover. We will now create one more action.
   ![Profiles](../graphics/Lab1_AI_Agent/2.17.png)

3. Click **Create New Action**. From the drop-down option, select **Fulfillment**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.18.png)

4. Configure it with name **_<copy>Create_New_Order</copy>_** and the Action description below.<br>
   > Action description: **_<copy>Collect medication order details, delivery address or pickup preference, total price, and respond with the order ID number once the order is completed. The request will contain the order details. From the order details let the attendee know the order ID.</copy>_**
   ![Profiles](../graphics/Lab1_AI_Agent/2.18a.png)

5. Scroll down and click to create **New input entity**. Fill up the table with the following and then click on **Add**. <br>
   > Entity Name: **_<copy>address</copy>_** <br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the attendee's delivery address — hotel name, room number.</copy>_**<br>
   > Example: **_<copy>Fairmont Austin or 101 Red River St, Austin, TX 78701</copy>_** <br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.png)

6. By following the same pattern, create an entity to collect the attendee's medication order details.<br>
   > Entity Name: **_<copy>orderDetails</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the OTC medication information that the attendee orders. Make sure to do correct math. If one unit of ibuprofen is 8 dollars and the attendee would like to buy 2 units then the price should be 16 dollars. Don't use double quotes (") in the generated responses.</copy>_**<br>
   > Example: **_<copy>Ibuprofen 200mg (2 units) and Acetaminophen 500mg (1 unit)</copy>_**<br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.1.png)   

7. By following the same pattern, create an entity to store the total price information of the order.<br>
   > Entity Name: **_<copy>orderTotal</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>After the attendee confirms whether they need delivery or pickup, and confirms they would like to proceed with completing the order, collect the Total information and assign it to this slot. Always use the number for the total. For example use 24 $ but not twenty-four dollars.</copy>_**<br>
   > Example: **_<copy>24 dollars, 18 dollars</copy>_**<br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.2.png)  

8. By following the same pattern, create an entity to store the order status information.<br>
   > Entity Name: **_<copy>status</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Always create it as "new"</copy>_**<br>
   > Example: **_<copy>new</copy>_**<br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.3.png)  

9. At this point you should see 4 created entities. Please double-check that your configuration matches the screenshot below.
    ![Profiles](../graphics/Lab1_AI_Agent/2.61.png)

10. Scroll down and for the **Fulfillment** option select **Manage in the source flow (voice only)**. Click **Save**.
   ![Profiles](../graphics/Lab1_AI_Agent/19.2.1.png)

11. **Publish** your AI Agent.
   ![Profiles](../graphics/Lab1_AI_Agent/19.33.png)

### Task 2. Configure fulfillment logic in the Voice flow.

1. In **Control Hub** go to Flows and open your flow with name **<copy>AutonomousAI_Flow_21209_<w class="attendee"></w></copy>**. Click on **Edit**.
   ![Profiles](../graphics/Lab1_AI_Agent/19.3.gif)

2. Remove **DisconnectContact** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.4.gif)


3. Add **HTTP Request** node and connect the Handled output from **VirtualAgentV2** to the **HTTP Request** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.14.gif)

4. Configure the **HTTP Request** with the following:

    - Use authenticated endpoint: **Off**
    - Request URL: **<copy>https://6a8f2a04a12b7de8cc0f5889.mockapi.io/customerOrder</copy>**
    - Method: **POST**
    - Content type: **Application/JSON**
       ![Profiles](../graphics/Lab1_AI_Agent/19.15.gif)

5. Configure the body of the HTTP request as the Metadata Activity output variable from the **VirtualAgentV2** node. Please see the pictures below.
   ![Profiles](../graphics/Lab1_AI_Agent/19.16.gif)

6. For this lab we are only using one fulfillment flow. To reconnect the call back to the AI agent and continue the conversation properly, we need to configure the event name. Click on the **VirtualAgentV2** node, scroll down to the bottom and copy the Activity output variable for the event name. Then in the same **VirtualAgentV2** node, open **State event** and paste it under **Event name**. See the pictures below.
   ![Profiles](../graphics/Lab1_AI_Agent/19.16.1.gif)

7. Next you need to bring the API call results back to your AI agent. For this, click on the **HTTP Request** node, scroll down on the right side and copy the name of the HTTPRequest...ResponseBody. Then go to the **VirtualAgentV2** node, open **State Events**, and insert the HTTP body response into **Event Data** inside of the {% raw %}{{}}{% endraw %}. See the steps on the gif below.
   ![Profiles](../graphics/Lab1_AI_Agent/19.17_.gif)

8. Enable decryption in the flow so you can monitor details of your further test calls.
   ![Profiles](../graphics/Lab1_AI_Agent/19.19.gif)

9. **Validate** and **Publish** the flow with the **Latest** tag.
   ![Profiles](../graphics/Lab1_AI_Agent/19.18.gif)

10. Place a test call to your test number. Ask to order OTC medication and provide the requested information. You should hear that the order was completed successfully. If not, use **Debugger** to troubleshoot.


<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>

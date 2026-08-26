---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 3: Configure Fulfillment Action and create a medication order using **Voice Flow**.

**<details><summary>What is fulfilment Action? <span style="color: orange;"></span></summary>**

Fulfillment Action is a task that an AI agent performs by understanding user intents and completes by connecting to external systems over API.


## </details>

## Mission overview

In this Mission you will be using the Voice flow to execute the API call to create the medication order with third party system.

![Profiles](../graphics/Lab1_AI_Agent/Fulfilment.png)

---

## Build

### Task 1. Configure Action in the AI Studio

1. Go to **Webex AI Agent AI** Studio Portal.

2. Select your AI agent with name **<copy><w class="attendee"></w>\_21209_AutoAI_Lab</copy>** that you created earlier and go to **Actions**. You will see one Action is already created by default for the Agent Handover. We will now create a few more actions.
   ![Profiles](../graphics/Lab1_AI_Agent/2.17.png)

3. Click on create <b>New Action</b>. From the drop-down option, select **Fulfillment**.
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
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.gif)

6. By following the same pattern, create an entity to collect the attendee's medication order details.<br>
   > Entity Name: **_<copy>orderDetails</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the OTC medication information that the attendee orders. Make sure to do correct math. If one unit of ibuprofen is 8 dollars and the attendee would like to buy 2 units then the price should be 16 dollars. Don't use double quotes (") in the generated responses.</copy>_**<br>
   > Example: **_<copy>Ibuprofen 200mg (2 units) and Acetaminophen 500mg (1 unit)</copy>_**<br>
   > Required: <b>Yes</b>

7. By following the same pattern, create an entity to store the total price information of the order.<br>
   > Entity Name: **_<copy>orderTotal</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>After the attendee confirms whether they need delivery or pickup, and confirms they would like to proceed with completing the order, collect the Total information and assign it to this slot. Always use the number for the total. For example use 24 $ but not twenty-four dollars.</copy>_**<br>
   > Example: **_<copy>24 dollars, 18 dollars</copy>_**<br>
   > Required: <b>Yes</b>

8. By following the same pattern, create an entity to store the order status information.<br>
   > Entity Name: **_<copy>status</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Always create it as "new"</copy>_**<br>
   > Example: **_<copy>new</copy>_**<br>
   > Required: <b>Yes</b>

9. At this point you should see 4 created entities. Please double check that your configuration matches the screenshot below.
    ![Profiles](../graphics/Lab1_AI_Agent/2.61.png)

10. Scroll down and for the **Fulfillment** option select **Manage in the source flow (voice only). Click **Save**
   ![Profiles](../graphics/Lab1_AI_Agent/19.2.png)

11. **Publish** your AI Agent.
   ![Profiles](../graphics/Lab1_AI_Agent/19.33.gif)

### Task 3. Configure fulfillment logic in the Voice flow.

1. In **Control Hub** go to Flows and open your flow with name **<copy>AutonomousAI_Flow_21209_<w class="attendee"></w></copy>**. Click on **Edit**.
   ![Profiles](../graphics/Lab1_AI_Agent/19.3.gif)

2. Remove **DisconnectContact** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.4.gif)

3. Create flow string variable with name **<copy>event_name</copy>** and empty default value.
   ![Profiles](../graphics/Lab1_AI_Agent/19.5.gif)

4. Create flow string variable with name **<copy>order_request_details</copy>** and empty default value.
   ![Profiles](../graphics/Lab1_AI_Agent/19.6.gif)

5. Add **SetVariable** node from the left side of flow designer to the field. Connect **VirtualAgentV2** node to the **SetVariable** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.7.gif)

6. Click on the **SetVariable** that you just created and configure your **event_name** variable to be assigned with **VirtualAgentV2....StateEventName** variable. </br>
   **Note:** *This event name will be the same as your Action name from the AI Agent Studio that is used for the fulfillment.*
   ![Profiles](../graphics/Lab1_AI_Agent/19.8.gif)

7. Add one more **SetVariable** node and connect them in series.
   ![Profiles](../graphics/Lab1_AI_Agent/19.9.gif)

8. We will need to assign the metadata from AI agent to the **order_request_details** string variable. To do so click on **VirtualAgentV2** node, on the right side scroll down until you will see Activity output variable. Copy the name of the variable related to MetaData. Go to your second SetVariable node and configure **order_request_details** with value of the Metadata that you copy inside of the {% raw %}{{}}{% endraw %}. See the gif below.
   ![Profiles](../graphics/Lab1_AI_Agent/19.10.gif)

9. Add **Case** node and connect **SetVariable** node to the **Case** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.11.gif)

10. Add **Disconnect Contact** and assign the **Default** output on **Case** node to the **Disconnect Contact**
   ![Profiles](../graphics/Lab1_AI_Agent/19.12.gif)

11. Click on **Case** node. Select **event_name** as the Case Variable. Remove the second Link Description. Keep only one Link Description, as for now you have only one action for fulfillment. In the Link Description provide the name of your action: **<copy>Create_Medication_Order</copy>**.
   **Note:** *If you add more actions later, the Case node is used as the distribution logic for different fulfillment requests.*
   ![Profiles](../graphics/Lab1_AI_Agent/19.13.gif)

12. Add **HTTP Request** node and connect the **Case** output link to the **HTTP Request** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.14.gif)

13. Configure the **HTTP Request** with the following:

    - Use authenticated endpoint: **Off**
    - Request URL: **<copy>https://67e9aa0bbdcaa2b7f5b9ed62.mockapi.io/customerOrder</copy>**
    - Method: **POST**
    - Content type: **Application/JSON**
    - Request body: **<copy>{% raw %}{{order_request_details}}{% endraw %}</copy>**
       ![Profiles](../graphics/Lab1_AI_Agent/19.15.gif)

14. Connect **HTTP Request** node to **VirtualAgentV2** node.
   ![Profiles](../graphics/Lab1_AI_Agent/19.16.gif)

15. Click on **VirtualAgentV2** node, open **State Event** and configure the **Event Name** as **<copy>{% raw %}{{event_name}}{% endraw %}</copy>**. In this case when the interaction returns to the AI agent it stays in the same session and AI agent continue the conversation accordingly.
   ![Profiles](../graphics/Lab1_AI_Agent/19.17.gif)

16. Next you need to bring the API call results back to your AI agent. For this, click on the **HTTP Request** node, scroll down on the right side and copy the name of the HTTPRequest...ResponseBody. Then go to **VirtualAgentV2** node, open the **State Events** insert the Http body response to the **Event Data** inside of the {% raw %}{{}}{% endraw %}. See the steps on the gif below.
   ![Profiles](../graphics/Lab1_AI_Agent/19.17_.gif)

17. Enable decryption in the flow so you can monitor your further test calls details.
   ![Profiles](../graphics/Lab1_AI_Agent/19.19.gif)

18. **Validate** and **Publish** the flow with the **Latest** tag.
   ![Profiles](../graphics/Lab1_AI_Agent/19.18.gif)

19. Place test call to your test number. Ask to order OTC medication, provide the requested information. You should hear that the order was completed successfully. Trace the call in the voice flow to make sure HTTP request was successful. Click on HTTP Request node, decrypt the results to make sure you got 201 status result.
   ![Profiles](../graphics/Lab1_AI_Agent/19.20.gif)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>

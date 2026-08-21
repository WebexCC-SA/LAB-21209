### AI Autonomous Agent Overview

The Autonomous AI Agent can handle various tasks, including:

- Natural Language Processing (NLP) — Understand and respond to human language in a natural and conversational manner.
- Decision making — Make informed choices based on available information and predefined rules.
- Automation — Automate repetitive or time-consuming tasks.

## Story

You are designing a Webex Autonomous AI agent for **Webex Event Health** — a health assistance service for event attendees traveling away from their regular healthcare providers. This AI agent will collect basic health information, recommend eligible OTC medications, schedule partner clinic appointments, arrange pharmacy pickup or hotel delivery, and escalate to a healthcare professional when predefined rules require it.</br></br>
Remember, **attendees will trust the AI Agent only when they truly believe it can assist them effectively**. That's exactly what you'll be working to achieve in this lab!

## Call Flow Overview

1. A new call enters the voice flow. </br>
2. The AI agent greets the attendee and collects basic information about their health needs. </br>
3. Based on the attendee's symptoms and requests, the AI agent recommends eligible OTC medications from the pharmacy catalog. </br>
4. The AI Agent can find a partner clinic and help schedule an appointment. </br>
5. The AI Agent creates medication orders and sends the information to a third-party system using APIs. </br>
6. The attendee receives SMS confirmation with order details. </br>
7. The attendee can always be transferred to a healthcare professional when escalation rules are met, along with the details of the conversation. </br>
8. The AI agent can use an external MCP server to look up pharmacy locations and check order status. </br>

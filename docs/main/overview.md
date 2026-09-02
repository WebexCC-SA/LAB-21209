---
#icon: material/folder-open-outline
icon: material/bullseye-arrow
---

## Get your login credentials

On your screen, look for the file named Credentials_21209_(ID). Open the file; you should see the following information:
   ![Profiles](../graphics/Lab1_AI_Agent/Login5.png)

As the next step, you need to set up your lab for your Attendee ID. In this case, you will all do configuration on the same tenant without interrupting other users.
<!-- Markdown content with embedded HTML -->
<div>
    <h3><b>Please submit the Attendee ID below.</b></h3> 
    <h3>All configuration entries in the lab guide will be renamed to include your Attendee ID.</h3>
    <form id="info">
        <label for="attendee">Attendee ID:</label>
        <input type="text" id="attendee" name="attendee" placeholder="Enter 3 digits" required>
        <button onclick="setValues()">Save</button>
    </form>

    <br>

    <p>Your stored Attendee ID is:<w class="attendee"> No ID stored</w></p>

</div>

## Overview of the Use Case

You are designing a **Webex AI Agent** for **Webex Event Health** — an AI-powered health assistance service for Cisco and Webex event attendees who are traveling and away from their regular healthcare providers.

Attendees can call a Webex AI Agent whenever they feel unwell or need healthcare assistance while attending an event.

[Webex AI Agent use case example](https://blog.webex.com/customer-experience/announcing-general-availability-of-webex-ai-agent-paving-way-new-era-cx/){:target="_blank"}

### Business Problem

While traveling to an event, attendees may:

- Feel sick and not know where to get care
- Be far from their family doctor
- Need a nearby doctor or clinic
- Need OTC medication
- Need medication delivered to their hotel

### Solution

The Webex AI Agent becomes a single point of contact through a voice call:

**Caller → Voice Call → Webex AI Agent → Healthcare Services**

## Disclaimer

The lab design and configuration examples provided are for educational purposes. For production design queries, please consult your Cisco representative or an authorized Cisco partner.

Let's get started and discover how **Webex AI Agent** delivers intelligent health assistance for event attendees!

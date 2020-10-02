# Who's On-Call Now Workflow
Not an integration, but something to help you keep on top of ever-changing on-call rotas. This workflow lets you enter a set of groups into the UI. Minutes later, someone gets an email detailing who is on call including escalations and nested groups.  Better still, you can schedule the report so it comes out every day. We acknowledge you can easily obtain this information in the xMatters UI. Go to Groups > Who's On Call and selects the groups you care about it. However, the UI has a maximum limit of 30 groups per query. And if you want to know the same information daily, why waste time dialling up the same report in the UI day-in day-out? 

---------

<kbd>
  <a href="https://support.xmatters.com/hc/en-us/community/topics">
  <img src="https://github.com/xmatters/xMatters-Labs/raw/master/media/disclaimer.png">
  </a>
</kbd>

---------


# Pre-Requisites
* xMatters account - If you don't have one, [get one](https://www.xmatters.com)!
* Some Groups set up with members, shifts, escalations etc.

# Files
* [WhosOnCallNow.zip](WhosOnCallNow.zip) - Who's On-Call Now workflow containing two forms, one flows and a custom step.  

# How it works
In the xMatters UI, navigate to Messaging > Who's On-Call Now > Who's on Call Now? Enter the list of groups you wish to query.  Set the separator character form a Choice of three; default is new line. You can use * as a wildcard chacter. Then press the big blue Send Message button.

<kbd>
  <img src="/media/wocn_form.png" width="750">
</kbd>

 It's OK to send this form without a recipient.
 
<kbd>
  <img src="/media/no_recipients.png" width="500">
</kbd>

Pop over to the Recent Events report. __Who's on Call Now initiated__ is there now, as that's the form you just sent. A minute later, you will see a second event __xMatters On Call Now [DATE]__ appear at the top of the events list. 

<kbd>
  <img src="/media/recent_events.png" width="500">
</kbd>

Hover your mouse on the right under the Date Started column. Click the little envelope icon that slides into place to view your report.

<kbd>
  <img src="/media/oncall_report.png" width="750">
</kbd>

Alternatively, you can configure so the report gets emailed to any user or group in your xMatters. See Installation Step 3 below.


# Installation

## xMatters set up
1. Log into xMatters as a user with the Developer role. Navigate to Workflows, click the Import button on the top right and import the [WhosOnCallNow.zip](WhosOnCallNow.zip) file.

2. Click the Open Workflow button. You will see a list of two forms. If other users are meant to use this, you will need to set Sender Permissions on both forms. To do this, click the left most button (says Web UI) and then Sender Permissions. Add the users or roles who can use the form.

<kbd>
  <img src="/media/sender_permissions.png" width="500">
</kbd>

3. Optional: If you want the results emailed to a user or group, you can set this on the __Who's On Call Now report__ form. Edit the form by clicking Edit > Layout. Add recipients to the Recipient box then save changes.

<kbd>
  <img src="/media/default_recipients.png" width="750">
</kbd>


4. Optional: There's a litle trick you can use to eliminate the No Recipients Selected warning when you initiate. First create an xMatters user called Nobody who has no devices. Open the __Who's On Call Now?__ form and set *Nobody* as recipient. You can also grey out the eye-icon to stop recipient from being displayed. Don't forget to Save Changes.
 
<kbd>
  <img src="/media/nobody" width="500">
</kbd>



# Testing
Execute a browser page reload, navigate to Messaging > Who's On-Call Now > Who's On Call Now? and give it a try.



# Troubleshooting
Debug logs are available. Navigate to the Who's On-Call Now workflows's Integration Builder tab, expand the Outbound integration section (Click where it says 1 Configured), then select Activity Stream from the right-hand gear icon. The Activity Stream contains logs.

<kbd>
  <img src="/media/activity_stream" width="500">
</kbd>


<kbd>
  <img src="/media/activity_logs" width="500">
</kbd>

You can also see the same logs via Flow Designer, although it takes a bit more clicking to get there. Navigate to the __FLOWS__ tab, cilck the __Who's On Call workflow__. When the canvas opens, click the Activity button on the top right of the screen, then click __Slack Who's On Call - Event Status Updates__, then click the Log tab.

<kbd>
  <img src="/media/flow_canvas" width="750">
</kbd>

The JavaScript code is contained within the __Who's On Call efficient__ custom step. You can access the code via the Flow tab > Custom draw on the right of the canvas. 

<kbd>
  <img src="/media/custom_step" width="500">
</kbd>

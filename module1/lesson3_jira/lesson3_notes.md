# SEIR Foundations — Module 1, Lesson 3

## Extra Credit — Jira and Slack Integration Notes

**Student:** Brent Johnson  
**Date:** November 16, 2026  
**AWS Region:** us-east-1 (Northern Virginia)  
**Jira Project:** BAI — Balerica AI Incident Management  
**Jira Site:** https://bsmoooth706.atlassian.net  
**Slack Channel:** #balerica-alerts

---

## BAM_5.5 — Jira and Slack Integration Verification

### Integration Explanation

The integration begins on my AWS EC2 instance, where the `incident.py` script processes an incident and coordinates the Jira and Slack components.

The script uses the Jira integration to create a ticket in the Balerica AI Incident Management project. Jira is contacted before Slack so that the notification can include the newly created issue key and a direct link to the ticket.

After Jira creates the issue, the integration sends an alert through the Slack component to the `#balerica-alerts` channel.

During my test, Jira successfully created issue **BAI-27**. The terminal confirmed the ticket creation with `jira_created: true` and reported the Slack delivery outcome as `slack_status: "sent"`.

I independently verified that BAI-27 appeared in Jira and that the corresponding notification, including its Jira link, appeared in Slack.

**Verified Jira Issue:** [BAI-27](https://bsmoooth706.atlassian.net/browse/BAI-27)

**Screenshot Evidence:** [BAM_5.5.jpg](screenshots/BAM_5.5.jpg)

### Troubleshooting Note

During configuration, my initial Jira verification returned an HTTP 404 error.

I investigated the Jira site URL and discovered a spelling error in the `.env` configuration.

After correcting the URL, I reran:

```bash
python3 jira.py --verify
```

The command successfully connected to the BAI project, confirming that the Jira configuration issue had been resolved.

### Lessons Learned

This exercise demonstrated the importance of checking environment variables and configuration settings when troubleshooting API connectivity. It also reinforced the need to independently verify successful automation by reviewing both the terminal output and the destination applications.

---

## BAM_5.6 — No Duplicate Tickets

### Objective

Verify that the incident management integration prevents duplicate Jira tickets and repeated Slack notifications when the same incident ID is submitted more than once.

### Test Procedure

I created and executed a Python script named `bam_dup_check.py`, using the same incident ID for both executions.

**Incident ID:** `BAM-DUP-BJ-001`

The script was executed twice:

```bash
python3 bam_dup_check.py
python3 bam_dup_check.py
```

### First Execution

The first execution successfully created Jira issue **BAI-28** and delivered an alert to Slack.

```text
incident_id: BAM-DUP-BJ-001
jira_key: BAI-28
jira_created: True
slack_status: sent
```

### Second Execution

During the second execution, the integration recognized the existing incident and did not create another Jira ticket or send an additional Slack notification.

```text
incident_id: BAM-DUP-BJ-001
jira_key: BAI-28
jira_created: False
slack_status: already_sent
```

### Verification Results

| Verification | First Execution | Second Execution |
|---|---|---|
| Incident ID | BAM-DUP-BJ-001 | BAM-DUP-BJ-001 |
| Jira issue | BAI-28 | BAI-28 |
| New Jira ticket created | Yes | No |
| Slack notification sent | Yes | No |
| Duplicate prevented | Not applicable | Yes |

I independently verified that only one Jira issue existed for the incident and that no additional Slack alert was delivered after the second execution.

**Verified Jira Issue:** [BAI-28](https://bsmoooth706.atlassian.net/browse/BAI-28)

**Screenshot Evidence:** [BAM_5.6.jpg](screenshots/BAM_5.6.jpg)

### Lessons Learned

This exercise demonstrated how duplicate detection helps prevent unnecessary Jira tickets and repeated Slack notifications.

I also learned the importance of **idempotency**, which allows an automated process to receive the same request multiple times without repeatedly creating the same result.

By recognizing the existing incident ID, the integration maintained a single Jira ticket and avoided sending redundant alerts.

---

## Extra-Credit Conclusion

The Jira and Slack integration exercises demonstrated a successful automated incident management workflow using AWS EC2, Python, Jira, and Slack.

I verified that incidents could generate Jira tickets, deliver Slack notifications containing issue links, and prevent duplicate tickets and notifications when the same incident was processed again.

These exercises strengthened my understanding of API integration, troubleshooting, automation, incident management, and the importance of verifying system behavior through multiple sources of evidence.
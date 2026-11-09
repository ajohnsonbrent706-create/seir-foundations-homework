# Lesson 2 — Slack Monitoring Homework

**Course:** SEIR Foundations  
**Module:** 1 — Lesson 2: Slack Monitoring  
**Date Completed:** November 8, 2026  
**AWS Region:** us-east-1 (N. Virginia)  
**EC2 Instance:** `i-0704ec4428f1f375e`  
**Instance Type:** `t3.small`  
**Operating System:** Amazon Linux  
**EC2 User:** `ec2-user`  
**Working Directory:** `/opt/balerica-bank`  
**Slack Channel:** `#balerica-alerts`

---

## 1. Objective

The objective of this assignment was to implement and test Python-based monitoring scripts capable of sending operational alerts from an AWS EC2 instance to Slack.

The assignment introduced severity-based notification filtering, server monitoring, disk utilization thresholds, incident simulation, and operational reporting.

All seven homework scripts were executed successfully, and the configuration experiments demonstrated how monitoring behavior changes according to administrator-defined settings.

## 2. EC2 Environment and Configuration

The homework was performed on an Amazon Linux EC2 instance using the `ec2-user` account and an activated Python virtual environment.

The shared `slack.py` helper handled alert delivery, while environment variables controlled notification availability and minimum severity.

The original configuration was restored after testing:

```ini
SLACK_ALERTS_ENABLED=TRUE
SLACK_ALERT_SEVERITY=INFO
```

The private Slack webhook URL was stored in `.env` and was not copied into the homework repository.

## 3. Homework Execution and Evidence

| Homework | Python Script | Result | Terminal Evidence | Slack Evidence |
|---|---|---|---|---|
| 1 — Hello Slack | `hw1_hello_slack.py` | Successful | [Terminal](screenshots/hw_hello_slack.png) | [Slack](screenshots/hw_slack_message.png) |
| 2 — Severity Tour | `hw2_severity_tour.py` | Successful | [Terminal](screenshots/hw2_severity_slack.png) | [Slack](screenshots/hw2_severity_slack_message.png) |
| 3 — Server Time | `hw3_server_time.py` | Successful | [Terminal](screenshots/hw3_server_time.png) | [Slack](screenshots/hw3_server_time_message.png) |
| 4 — Disk Watch | `hw4_disk_watch.py` | Successful | [Terminal](screenshots/hw4_disk_watch.png) | [Slack](screenshots/hw4_disk_watch_message.png) |
| 5 — Load Check | `hw5_load_check.py` | Successful | [Terminal](screenshots/hw5_load_check.png) | [Slack](screenshots/hw5_load_check_message.png) |
| 6 — Incident Drill | `hw6_incident_drill.py` | Successful | [Terminal](screenshots/hw6_incident_drill.png) | [Slack](screenshots/hw6_incident_drill_message.png) |
| 7 — Morning Report | `hw7_morning_report.py` | Successful | [Terminal](screenshots/hw7_morning_report.png) | [Slack](screenshots/hw7_morning_report_message.png) |

### Homework 1 — Hello Slack

**Incident ID:** HW-001

The first script verified connectivity between the EC2 instance and the Slack workspace.

The script successfully delivered an INFO notification to `#balerica-alerts`, confirming that the webhook configuration and Python alert helper were functioning.

**What I learned:** A basic connectivity test is an important prerequisite before deploying more advanced monitoring agents. It helps isolate configuration problems from application logic.

### Homework 2 — Severity Tour

**Incident ID:** HW-002

This script demonstrated four notification severity levels: INFO, WARNING, ERROR, and CRITICAL.

I observed how changing the minimum severity threshold affected which alerts were delivered.

**What I learned:** Severity filtering allows monitoring systems to prioritize notifications according to operational importance, reducing unnecessary alerts while maintaining visibility into significant incidents.

### Homework 3 — Server Time

**Incident ID:** HW-003

The script generated an INFO notification containing the server's UTC timestamp.

**Observed UTC timestamp:** November 9, 2026, 00:20:59 UTC.

**What I learned:** UTC provides a consistent time reference across servers operating in different geographical regions. Standardized timestamps help engineers correlate logs, investigate incidents, and establish accurate event timelines.

### Homework 4 — Disk Watch

**Incident ID:** HW-004

The script measured root filesystem utilization using Python's `shutil.disk_usage()` function.

**Observed results:**

- Disk utilization: 25.4%
- Available storage: Approximately 5.9 GB
- Original WARNING threshold: 75%
- ERROR threshold: 90%
- Original alert severity: INFO

**Why is a quiet INFO notification good design?**

A quiet INFO notification indicates that the monitored resource is operating within acceptable limits. It provides useful operational visibility without unnecessarily escalating normal activity.

Good monitoring distinguishes healthy system behavior from conditions requiring investigation.

### Homework 5 — Load Check

**Incident ID:** HW-005

The script examined Linux system load averages and compared them with available CPU resources.

**Observed results:**

- 1-minute load average: 0.00
- 5-minute load average: 0.00
- 15-minute load average: 0.00
- Available virtual CPUs: 2
- Alert severity: INFO

**What could cause a sudden increase in CPU load?**

A spike in system load may result from computationally intensive applications, background jobs, inefficient processes, unexpected traffic, or excessive concurrent workloads.

Load averages should be interpreted in relation to the number of available CPUs and other system performance metrics.

### Homework 6 — Incident Drill

The incident drill simulated operational events affecting banking infrastructure.

Five simulated incidents were generated and successfully delivered to Slack.

| Incident ID | Severity | Simulated Event |
|---|---|---|
| DRILL-8691 | WARNING | SWIFT queue contained 42 waiting messages |
| DRILL-3914 | CRITICAL | Account lookup ledger became unreachable |
| DRILL-4735 | INFO | Nightly ledger backup completed |
| DRILL-5006 | ERROR | Payment posting rejection rate exceeded 5% |
| DRILL-3471 | WARNING | COBOL batch processing delayed by 12 minutes |

**Which incidents would justify waking an engineer at 3 AM?**

The CRITICAL account lookup ledger outage would justify immediate escalation because it could prevent essential banking operations.

The ERROR payment rejection incident could also require urgent escalation if it affected a significant volume of customer transactions.

A completed backup would not ordinarily justify waking an engineer, while the SWIFT queue and COBOL delay would require additional context about their business impact and duration.

### Homework 7 — Morning Report

**Incident ID:** HW-007

The final script generated a system health summary and delivered it to Slack.

**Observed results:**

- UTC timestamp: November 9, 2026, 00:59:00 UTC
- Local time: November 8, 2026, approximately 7:59 PM EST
- Operating system: Linux
- Architecture: x86_64

## Experiment Execution and Screenshot Evidence

| Experiment | Configuration / Modification | Expected Result | Actual Result | Terminal Evidence | Slack Evidence |
|---|---|---|---|---|---|
| 1A — CRITICAL Severity | `SLACK_ALERT_SEVERITY=CRITICAL` | 1 CRITICAL alert | 1 CRITICAL delivered; INFO, WARNING, and ERROR suppressed | [Terminal](screenshots/experiment_severity_critical_terminal.png) | [Slack](screenshots/experiment_severity_critical_message.png) |
| 1B — WARNING Severity | `SLACK_ALERT_SEVERITY=WARNING` | 3 alerts: WARNING, ERROR, CRITICAL | Filtering tested; exact count pending verification | [Terminal](screenshots/experiment_severity_warning.png) | [Slack](screenshots/experiment_severity_warning_message.png) |
| 1C — ERROR Severity | `SLACK_ALERT_SEVERITY=ERROR` | 2 alerts: ERROR, CRITICAL | 2 alerts reported | [Terminal](screenshots/experiment_severity_error.png) | [Slack](screenshots/experiment_severity_error_message.png) |
| 2 — Slack Kill Switch | `SLACK_ALERTS_ENABLED=false` | No Slack notifications | Script skipped delivery; no new notification observed | [Terminal](screenshots/experiment_t:f.png) | [Slack](screenshots/experiment_t:f_nomessage.png) |
| 3 — Disk WARNING Threshold | WARNING threshold reduced from 75% to 20% | WARNING at 25.4% disk usage | WARNING delivered successfully | [Terminal](screenshots/experiment_disk.png) | [Slack](screenshots/experiment_disk_message.png) |
| 4 — Configuration Restoration | Re-enable Slack; restore INFO severity and original disk thresholds | INFO notification delivered | INFO delivered successfully | [Terminal](screenshots/experiment_restoration.png) | [Slack](screenshots/experiment_restoration_message.png) |

### Experiment Summary

The four experiment categories demonstrated the behavior of the Slack monitoring system under different configurations.

**Experiment 1 — Severity Filtering:** Tested CRITICAL, WARNING, and ERROR minimum severity thresholds to observe how lower-priority alerts were suppressed.

**Experiment 2 — Slack Kill Switch:** Verified that disabling Slack notifications prevented the monitoring script from delivering alerts.

**Experiment 3 — Disk Threshold Modification:** Lowering the disk WARNING threshold from 75% to 20% caused the existing 25.4% disk utilization measurement to generate a WARNING notification.

**Experiment 4 — Configuration Restoration:** Restored the original notification settings and disk thresholds. The disk monitoring script returned to INFO severity and successfully delivered its notification.

**Final configuration:**
- `SLACK_ALERTS_ENABLED=TRUE`
- `SLACK_ALERT_SEVERITY=INFO`
- Disk WARNING threshold: 75%
- Disk ERROR threshold: 90%

**Overall Result:** All four experiment categories were completed, and the original monitoring configuration was restored.
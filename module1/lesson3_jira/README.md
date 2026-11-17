# SEIR Foundations — Module 1, Lesson 3: Jira

## A Day in My Shoes

**Student:** Brent Johnson  
**Date of Activities:** Monday, November 16, 2026  
**Jira Space:** SEIR-Saga_BrentJohnson  
**Jira Project Key:** SSB  
**Epic:** SSB-1 — A day in my shoes  
**Repository:** seir-foundations-homework

## 1. Assignment Overview

The purpose of this assignment was to practice Agile project management using Jira by documenting a typical day through an Epic, Stories, and Tasks.

I organized my daily activities into eight Stories covering personal routines, grocery shopping, coursework, household responsibilities, and handyman work. Each Story was divided into individual Tasks with descriptions, scheduled times, and story point estimates.

## 2. Jira Work Item Summary

| Work Type | Total Created | Total Story Points |
|---|---:|---:|
| Epic | 1 | — |
| Stories | 8 | 36 |
| Tasks | 38 | 66 |

**Total Jira work items:** 47

Story estimates and Task estimates are tracked separately.

## 3. Epic Evidence

| Jira Key | Work Type | Summary | Screenshot |
|---|---|---|---|
| SSB-1 | Epic | A day in my shoes | [View Epic](screenshots/jira_epic.jpg) |

## 4. Story Evidence

| Jira Key | Story Summary | Story Points |
|---|---|---:|
| SSB-2 | Morning personal routine | 2 |
| SSB-6 | Breakfast and grocery shopping | 5 |
| SSB-15 | SEIR coursework and study sessions | 8 |
| SSB-21 | Organize work truck and complete laundry | 5 |
| SSB-27 | Walk dog and prepare for appointment | 3 |
| SSB-33 | Complete garbage disposal service appointment | 8 |
| SSB-39 | Dinner and household responsibilities | 3 |
| SSB-45 | Evening wind-down and bedtime | 2 |
| **Total** | **8 Stories** | **36** |

**Story Screenshot:** [View Story Evidence](screenshots/jira_story.jpg)

## 5. Task Evidence

| Jira Key | Task Summary | Points |
|---|---|---:|
| SSB-3 | Wake up and use restroom | 1 |
| SSB-4 | Take shower and brush teeth | 1 |
| SSB-5 | Get dressed | 1 |
| SSB-7 | Make coffee and check breakfast supplies | 1 |
| SSB-8 | Drive to grocery store | 2 |
| SSB-9 | Purchase breakfast and dinner items | 2 |
| SSB-10 | Drive home from grocery store | 2 |
| SSB-11 | Put away groceries and clean dishes | 1 |
| SSB-12 | Prepare breakfast and set table | 2 |
| SSB-13 | Eat breakfast and watch YouTube | 1 |
| SSB-14 | Load dishwasher and clean kitchen | 2 |
| SSB-16 | Read Head First Agile Chapters 4 and 5 | 3 |
| SSB-17 | Resume coursework and remaining reading | 3 |
| SSB-18 | Review Agile instructional videos and additional reading | 2 |
| SSB-19 | Review Jira homework and extra-credit opportunities | 2 |
| SSB-20 | Resume evening coursework and study session | 3 |
| SSB-22 | Clean work truck | 3 |
| SSB-23 | Organize tools and work supplies | 2 |
| SSB-24 | Start colored laundry | 1 |
| SSB-25 | Transfer colored laundry to dryer and start whites | 1 |
| SSB-26 | Transfer white laundry to dryer | 1 |
| SSB-28 | Walk dog around neighborhood | 2 |
| SSB-29 | Prepare for service appointment | 1 |
| SSB-30 | Double-check tools and equipment | 1 |
| SSB-31 | Contact tenant to confirm appointment | 1 |
| SSB-32 | Check Apple Maps and traffic conditions | 1 |
| SSB-34 | Drive to Home Depot | 3 |
| SSB-35 | Purchase replacement garbage disposal | 2 |
| SSB-36 | Travel to tenant's apartment | 1 |
| SSB-37 | Remove and replace garbage disposal | 5 |
| SSB-38 | Drive home after service appointment | 3 |
| SSB-40 | Update Jira homework progress | 2 |
| SSB-41 | Eat dinner | 1 |
| SSB-42 | Turn on Monday Night Football | 1 |
| SSB-43 | Wash dishes and clean kitchen | 1 |
| SSB-44 | Fold clean laundry | 1 |
| SSB-46 | Continue studying while football plays | 2 |
| SSB-47 | Finish evening activities and go to bed | 1 |
| **Total** | **38 Tasks** | **66** |

**Task Screenshot:** [View Task Evidence](screenshots/jira_task.jpg)

## 6. Largest Task Estimate

**Jira Issue:** SSB-37  
**Task:** Remove and replace garbage disposal  
**Story Points:** 5

I assigned this Task five story points because replacing a garbage disposal requires multiple steps, technical knowledge, and careful attention to safety. The work includes removing the existing unit, installing the replacement, checking the plumbing and electrical connections, and testing the installation for proper operation and leaks.

This Task received a higher estimate than the other activities because unexpected installation problems could increase its complexity and completion time.

## 7. Jira Estimation and Backlog Evidence

| Requirement | Screenshot |
|---|---|
| Story point estimation enabled | [View Estimation Settings](screenshots/jira_estimation_on.jpg) |
| Epic created | [View Epic](screenshots/jira_epic.jpg) |
| Story created and estimated | [View Story](screenshots/jira_story.jpg) |
| Task created and estimated | [View Task](screenshots/jira_task.jpg) |
| Jira Backlog | [View Backlog](screenshots/jira_backlog.jpg) |

## 8. Reflection

This assignment helped me understand how Jira organizes work using Epics, Stories, and Tasks. I learned how to break larger activities into smaller, manageable work items and assign story point estimates based on their relative complexity.

Using Jira to organize my daily routine also helped me recognize how Agile project management concepts can be applied to everyday responsibilities, not just software development projects.

---

## 9. Extra Credit — Jira Integration with AWS EC2 and Slack

### Overview

For the Lesson 3 extra-credit exercises, I configured and tested an integration between an AWS EC2 instance, Jira, and Slack using Python scripts provided for the SEIR Foundations Balerica AI incident management lab.

The objective was to verify that the EC2 environment could communicate with Jira and Slack, automatically create an incident ticket, send an alert containing the Jira issue link, and prevent duplicate notifications when the same incident was reported again.


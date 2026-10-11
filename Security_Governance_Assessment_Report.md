# GRC102 · Information Security Governance
## Security Governance Simulation — Week 5 | Practical Lab 8 | Equifax-Inspired Scenario

**Monitoring, Control Verification, Metrics and Executive Reporting**

---

| Field | Detail |
|---|---|
| **Student** | Hilda Odein Joshua-Jack |
| **Reg. No** | C11/26/CGRCE/17247 |
| **Cohort** | Cohort 11 |
| **Course** | GRC102 – Information Security Governance |
| **Assessment** | Linux Audit, Security Monitoring and Control Assurance |
| **Environment** | Kali GNU/Linux Rolling 2026.2 • VirtualBox |
| **Submission date** | 11 October 2026 |

---

## Supporting Artefact Map

| Part | Known project artefacts |
|---|---|
| Part 1 | `docker-compose.yml`; `vulnerability_scanner.py`; `vulnerability_report_20261011_002639.json`; `vulnerability_report_20261011_012206.json`; `vulnerability_report_20261011_013905.json`; `governance_tracker.py`; `governance_data.json`; `executive_dashboard.html` |
| Part 2 | `simulate_attack.py`; `attack_log.json`; `analyze_governance_failures.py`; `governance_failure_report_20261011_010159.json`; `equifax_comparison.md` |
| Part 3 | `implement_governance_controls.py`; `governance_controls_report.md`; `initialize_governance.py`; `patch_management.py`; `governance_oversight.md` |
| Part 4 | `governance_metrics.py`; `executive_dashboard.html`; `board_report.md`; `governance_metrics_framework.md`; `dashboard_user_guide.md`; `metrics_visualizations/` |

---

## Executive Summary

This practical uses an isolated Docker-based scenario to examine how technical weaknesses can become material security and governance risks when ownership, remediation, monitoring, access control and executive oversight do not work together. The environment is intended to support safe review of service configuration, synthetic data, vulnerability findings and governance processes; it is not a production environment.

The project artefacts cover baseline scanning, governance tracking, synthetic event simulation, governance failure analysis, control implementation and metrics-based reporting. A key principle is that **a control should not be considered effective merely because a policy, script or configuration exists**. Effectiveness requires accountable ownership, defined criteria, evidence of implementation, a repeatable test, a recorded result and follow-up when a control fails.

The Equifax comparison is thematic. Public investigations described issues involving vulnerability remediation, detection, database access and data governance. The simulation helps analyse these failure patterns, but it does not establish that Equifax's systems have been recreated or that every control in this lab passed. **Untested items must remain open evidence gaps.**

### Scope and Limitations

| In scope | Important limitations |
|---|---|
| Docker Compose configuration review; scenario scan; governance tracker; synthetic event simulation; governance failure analysis; control design and available verification; metrics and reporting. | No real customer data or external target is required. The lab does not execute the Equifax exploit, deploy Apache Struts, or independently prove production-grade SIEM coverage. Runtime status requires actual test evidence. |

---

## Part 1 — Setting Up a Simulated Environment

### 1.1 Environment and Architecture

The lab is intended to run in an isolated Linux environment using Docker Compose. The web application is configured for local host access on `127.0.0.1:8080`. The database port is not intended to be published directly to the host, and sample records should be synthetic. These boundaries reduce risk while allowing review of service configuration, application health and internal communication.

The baseline environment supports examination of governance concerns such as broad internal reachability, example credentials, limited monitoring evidence or missing remediation ownership. The actual state of the containers is established from the captured output of `sudo docker-compose ps`.

<div align="center" style="border: 2px solid #333; border-radius: 6px; padding: 15px; margin: 20px auto; max-width: 900px;">

**FIGURE 1 | DOCKER SERVICES AND STATE**

<img width="602" height="221" alt="image" src="https://github.com/user-attachments/assets/b9fd0a55-d8a5-4e18-8264-f32be7a42cc7" />

<p><em>01-docker-compose-ps.png</em></p>

</div>


<div align="center" style="border: 2px solid #333; border-radius: 6px; padding: 15px; margin: 20px auto; max-width: 900px;">

**FIGURE 2 | APPLICATION HEALTH CHECK**

<img width="601" height="168" alt="image" src="https://github.com/user-attachments/assets/4a5ec54d-4048-49d6-a1a4-47f288e88c21" />

*02-application-health.png*

</div>

### 1.2 Vulnerability Scan Report

The project contains a vulnerability-scanning script and timestamped JSON report outputs.

| Issue to assess | Governance significance | Evidence / follow-up |
|---|---|---|
| Patch and vulnerability lifecycle | Findings need an owner, severity-based deadline, approved exceptions where needed and a retest before closure. | Reference actual finding IDs and severity ratings from the vulnerability scan. Record ownership, remediation and retest results in the governance tracker. |
| Network exposure | Published ports and service-to-service access should follow the intended architecture and least privilege. | The observed Docker output confirms that `web_server` is published on `0.0.0.0:8080` and `[::]:8080`. Review the effective Compose configuration and service/network output to determine whether this exposure is justified. |
| Credentials and database access | Example credentials and environment variables are not a production secrets-management design. | Inspect the Compose configuration and relevant environment settings. Document the actual configuration without exposing passwords. Identify production requirements for secrets management, credential rotation and database access control. |

**Figure 3 — Vulnerability Scan and Finding Summary**

![Baseline scan](screenshots/03-baseline-scan.png)

### 1.3 Governance Tracker Dashboard

The governance tracker organises risks, controls, incidents, metrics and follow-up actions. Its value depends on linking each issue to an accountable owner, due date, status, evidence and escalation path.

**Figure 4 — Governance Tracker Dashboard**

![Governance tracker dashboard](screenshots/04-governance-tracker.png)

### 1.4 Explanation: How the Simulated Environment Reflects the Equifax Breach

The simulation reflects an important governance lesson from the Equifax breach: **a known technical exposure can remain dangerous when asset ownership, patch deployment, monitoring and management follow-up are not connected into one reliable process.** Public investigations described failures involving vulnerability identification and remediation, detection, database access and data governance. In the lab, the baseline configuration and governance tracker provide a practical way to examine how a technical finding should become an owned risk, a time-bound remediation action and a verified closure decision (U.S. Government Accountability Office [GAO], 2018; U.S. House Committee on Oversight and Government Reform, 2018).

The lab is a simplified, isolated simulation. It does not reproduce Equifax's architecture, run the Apache Struts exploit, or prove that the original attack path has been recreated. Its value is demonstrating governance conditions that can allow a weakness to persist: incomplete visibility, broad trust between components, weak remediation evidence and insufficient escalation. The lesson is to assess both the technical state and the management process that ensures weaknesses are identified, corrected and independently verified.

---

## Part 2 — Analyzing Security Governance Failures

### 2.1 Attack Simulation Log

The project includes `simulate_attack.py` and `attack_log.json`. The exercise is a synthetic suspicious-event simulation, not a real intrusion. It is intended to test whether an event can be recorded, analysed, assigned, escalated and used to identify weaknesses in the governance process.

**Figure 5 — Synthetic Attack/Event Log**

![Synthetic attack log](screenshots/05-synthetic-attack-log.png)

### 2.2 Governance Failure Analysis

The analysis script and generated JSON report structure findings around technical conditions and the governance process needed to manage them. Each finding should identify evidence, potential business impact, owner, recommended action, due date and verification method.

| Governance theme | Failure pattern to assess | Expected response |
|---|---|---|
| Patch management | A finding is not linked to an inventory, owner, deadline and retest. | Prioritise by severity/exposure; assign an owner; track remediation and exceptions; retest. |
| Monitoring and detection | Logs may exist without evidence of alerting, investigation, ownership or escalation. | Define sources, alert use cases, triage SLAs, incident owner and closure evidence. |
| Network segmentation | Application and database services may have broader reachability than necessary. | Separate trust zones and test allowed and denied paths. |
| Database access and data governance | Broad access or weak secrets handling can increase the impact of application compromise. | Apply least privilege, protect and rotate secrets, restrict administration and audit access. |
| Accountability and oversight | Findings can remain unresolved when ownership, exception approval and reporting are unclear. | Record decisions, escalate overdue material risks and report residual risk. |

**Figure 6 — Governance Failure Analysis Output**

![Governance failure analysis](screenshots/06-governance-failure-analysis.png)

### 2.3 Comparison with the Equifax Case Study

| Dimension | Equifax lesson | Simulation can demonstrate | Limit |
|---|---|---|---|
| Vulnerability management | A critical weakness can remain exploitable when identification and patching do not result in remediation. | Assign, time-bound, track and retest findings. | The lab does not deploy Apache Struts or verify its patch level. |
| Detection | Ineffective monitoring can reduce visibility into malicious activity. | Define log sources, alerts, owners and response evidence. | A synthetic event log does not prove SIEM coverage. |
| Segmentation and data access | Weak separation and access controls can increase the reach of compromise. | Limit and test network paths and database access. | Configuration is design evidence; runtime tests remain necessary. |
| Governance and accountability | Policies are insufficient without operational execution and oversight. | Assign owners, deadlines, escalation and reporting. | A simulated tracker does not prove real organisational maturity. |

> **NOTE:** `equifax_comparison.md` is a supporting artefact. This master report summarises its themes; the full comparison report remains useful for traceability.

### 2.4 Explanation: Key Governance Lessons Learned

The main lesson is that **governance failures often occur in the gap between a documented requirement and its execution**. A patching policy is not enough unless the organisation knows which assets are affected, assigns responsibility, sets deadlines, manages exceptions and verifies the fix. Similarly, a monitoring requirement is incomplete without defined log sources, alert logic, response ownership, escalation criteria and evidence that events are investigated and closed. These are connected governance processes, not separate technical tasks.

A second lesson is to **distinguish a control that is designed from one that is configured and one that is operating effectively**. A script or configuration file can show intent, but only an appropriate test and reviewable evidence support a conclusion about effectiveness. Untested items should remain open, with additional evidence needs documented. This approach is consistent with risk-based governance and the Govern, Identify, Protect, Detect, Respond and Recover outcomes in the NIST Cybersecurity Framework 2.0 (Pascoe et al., 2024).

---

## Part 3 — Implementing Security Governance Controls

### 3.1 Control Implementation Approach

The project includes `implement_governance_controls.py`, `initialize_governance.py`, `patch_management.py` and a governance controls report. The controls are intended to turn identified failure patterns into assigned, trackable actions, covering patch and vulnerability management, network segmentation, database access, monitoring and governance oversight.

| Control area | Expected design | Evidence needed for effectiveness |
|---|---|---|
| Patch management | Asset ownership, severity-based SLAs, change tracking, exception approval and retesting. | Affected component/version, approved change, deployment evidence and post-change retest. |
| Network segmentation | Separate frontend and data-tier trust zones; expose only required ports. | Effective configuration, network membership and allowed/denied reachability tests. |
| Database security | Least-privilege identities, protected/rotated secrets, restricted administration and audit records. | Configuration review and authorised/unauthorised access tests where safely available. |
| Monitoring and response | Defined sources, detections, alert ownership, triage SLA, escalation and closure evidence. | Evidence an event reaches the monitoring path, triggers an alert, is assigned and investigated. |
| Governance oversight | Control owners, risk acceptance authority, escalation thresholds and executive reporting. | Documented responsibilities, decisions, overdue-risk reporting and review records. |

**Figure 7 — Hardened Environment and Network Configuration (Control Implementation)**

![Hardened environment](screenshots/07-hardened-environment.png)

**Figure 8 — Control Verification Results**

![Control verification](screenshots/08-control-verification.png)

**Figure 9 — Attack Simulation Results**

![Attack simulation](screenshots/09-attack-simulation.png)

### 3.2 Control Assurance and Residual Risk

The controls report should separate design evidence from runtime evidence. If a control is in a script or configuration but the relevant test was not performed, report it as **not tested**. A sample database password is a teaching artefact, and environment variables are not a substitute for a production secrets manager. Network separation should be verified with actual permitted and denied communication tests. A synthetic event workflow should not be described as a full SIEM or real-time detection deployment.

| Status | Meaning | Reporting approach |
|---|---|---|
| PASS | Defined test ran and produced expected result. | State test, actual output, date and evidence reference. |
| FAIL | Test ran and expected outcome was not achieved. | Record impact, owner, remediation and retest date. |
| NOT TESTED | No test was run or required evidence was unavailable. | Keep open and state the evidence needed. |
| MANUAL TEST REQUIRED | Human review or test outside the script is necessary. | Name reviewer/owner and document planned verification. |

### 3.3 Explanation: How Implemented Controls Address Equifax Governance Failures

The implemented control design addresses governance patterns identified in the Equifax case study by linking technical findings to ownership, deadlines, remediation evidence and oversight. **Patch management** creates a structured route from identifying a weakness to assigning an owner, tracking a change and retesting the affected component. **Network segmentation and database-access controls** are intended to reduce unnecessary reachability and limit the potential impact of application compromise. **Monitoring controls** define the need to record events, assign triage responsibility and escalate material issues rather than relying on logs existing in isolation.

**Governance oversight and reporting** provide the management layer needed to sustain these controls. Exceptions and overdue high-risk findings should remain visible to authorised decision-makers, and closure should require evidence that remediation worked. These controls respond to the lessons of Equifax; they are not proof that every risk has been eliminated. Report each control according to evidence captured, disclose tests not performed and preserve residual risks for follow-up.

---

## Part 4 — Developing Security Governance Metrics and Reporting

**Required deliverables:** security governance metrics script; executive dashboard HTML file; board report; metrics framework; dashboard user guide; dashboard and visualisation screenshots; and a 1–2 paragraph explanation of how metrics and reporting support effective security governance.

### 4.1 Metrics Framework

The project includes `governance_metrics.py`, `governance_metrics_framework.md`, `executive_dashboard.html`, `board_report.md`, `dashboard_user_guide.md` and the `metrics_visualizations/` directory. Each metric should have a formula, target, data source, reporting frequency, accountable owner and intended audience.

| Metric | Management question | Governance follow-up |
|---|---|---|
| Patch compliance | Are applicable systems patched within the agreed period? | Investigate missed targets and assign owners. |
| Remediation time | How long do material findings remain open? | Escalate overdue critical/high findings and blockers. |
| Overdue high-risk findings | What material risks remain unresolved? | Require owner, due date, exception decision and executive visibility. |
| Control test pass rate | Do sampled controls meet defined criteria? | Analyse repeat failures and verify remediation. |
| Monitoring coverage | Are critical systems and required event sources covered? | Identify unmonitored assets and track onboarding/testing. |
| MTTA / MTTC | How quickly are events acknowledged and contained/closed? | Review response bottlenecks and process needs. |
| Policy review currency | Are policies reviewed and approved on schedule? | Escalate overdue reviews and confirm owner approval. |
| Risk-exception currency | Do accepted risks have valid approval and review dates? | Renew, remediate or revoke expired exceptions. |

**Figure 10 — Security Governance Metrics**

![Security governance metrics script](screenshots/10-security-governance-metrics-script.png)

### 4.2 Executive Dashboard and Visualisations

The HTML dashboard is intended to give leaders a concise view of security posture, material risks, compliance/control status, trends and recommended actions. Open `executive_dashboard.html` in a browser and confirm that its values and visualisations match the current metrics output. Red/amber/green indicators should draw attention to risk; **they must not hide missing data or make an untested control appear effective.**

**Figure 11 — Executive Dashboard Overview**

![Executive dashboard](screenshots/11-executive-dashboard.png)

**Figure 12 — Metric Detail: Security Monitoring Coverage Trend**

![Security monitoring coverage trend](metrics_visualizations/12-security-monitoring-coverage-trend.png)

**Figure 13 — Metric Detail: Patch Compliance Trend**

![Patch compliance trend](metrics_visualizations/13-patch-compliance-trend.png)

**Figure 14 — Metric Detail: Policy Compliance Trend**

![Policy compliance trend](metrics_visualizations/14-policy-compliance-trend.png)

**Figure 15 — Metric Detail: Security Incidents Trend**

![Security incidents trend](metrics_visualizations/15-security-incidents-trend.png)

**Figure 16 — Metric Detail: Vulnerability Remediation Time Trend**

![Vulnerability remediation time trend](metrics_visualizations/16-vulnerability-remediation-time-trend.png)

### 4.3 Board Report

The board report should summarise material risks, evidence gaps, trends and decisions required. Recommendations should name an accountable role and due date. Board reporting should expose overdue exceptions, residual risk and verification status, not only report that a tool has been deployed. The `board_report.md` is retained as the supporting artefact.

### 4.4 Dashboard User Guide

The user guide explains how to open the HTML dashboard, interpret status indicators, read visualisations, prioritise action and refresh reporting after running the metrics script. It matches the current dashboard layout and script behaviour.

### 4.5 Explanation: How Metrics and Reporting Support Effective Security Governance

Metrics help security governance move from general statements about security to measurable questions leaders can act on. **Patch compliance and remediation time** show whether weaknesses are addressed promptly; **overdue high-risk findings and expired exceptions** reveal unresolved risk; **control-test results and monitoring coverage** help show whether safeguards are operating and important systems are visible. When definitions, targets, owners, sources and reporting frequency are documented, results can be compared over time and challenged consistently.

The executive dashboard and board report turn those measures into decisions. They help leadership prioritise resources, escalate persistent failures, challenge risk acceptance and track remediation. **Metrics must be interpreted with their limitations: incomplete source data, synthetic records or untested controls must be labelled, not presented as proof of success.** Effective reporting combines concise performance information with traceable evidence, accountable owners, due dates and follow-up on residual risk.

---

## Overall Conclusion

This lab demonstrates how security governance can connect technical findings with management accountability, control implementation, monitoring and executive reporting. The four parts form a lifecycle: **establish a safe environment, analyse governance failures, implement controls that address them, and measure whether risks are being managed effectively.**

The key outcome is not simply the presence of scripts, dashboards or policies. A defensible governance process makes risks visible, assigns responsibility, sets deadlines, records decisions and verifies remediation. Before submission, insert actual screenshots, validate quoted statuses and metrics, ensure supporting artefacts are in the repository, and submit the completed master document through the course LMS.

---

## References

Docker, Inc. (n.d.). *Docker Compose documentation*. https://docs.docker.com/compose/

National Institute of Standards and Technology. (2024). *The NIST Cybersecurity Framework (CSF) 2.0* (NIST CSWP 29). https://doi.org/10.6028/NIST.CSWP.29

U.S. Government Accountability Office. (2018). *Data protection: Actions taken by Equifax and federal agencies in response to the 2017 breach* (GAO-18-559). https://www.gao.gov/products/gao-18-559

U.S. House Committee on Oversight and Government Reform. (2018, December 10). *Committee releases report revealing new information about the Equifax data breach*. https://oversight.house.gov/report/committee-releases-report-revealing-new-information-about-equifax-data-breach/

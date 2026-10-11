
# Security Governance Controls Implementation Report

## 1. Overview

This report documents the implementation of security governance controls in the simulated security environment. The controls were designed to address weaknesses associated with vulnerability management, network segmentation, database security, security monitoring, and governance oversight.

The implementation was performed using the `implement_governance_controls.py` script within the `security_governance_lab` directory. The script invoked the patch management utility, updated the governance tracker, created monitoring and oversight files, and initiated verification through a vulnerability scan.

## 2. Implemented Security Governance Controls

### 2.1 Patch Management Controls

**Control:** Automated Patch Management  
**Control ID:** CTL-004  
**Related Policy:** POL-001  
**Responsible Role:** Security Engineer

The patch management process was invoked to simulate the application of the Apache Struts 2 security patch associated with CVE-2017-5638. The objective was to address the vulnerability exploited in the Equifax data breach by establishing a structured approach to identifying and applying security updates.

A critical patch compliance metric was also added to the governance tracker. The metric is intended to measure the percentage of systems receiving critical patches within seven days.

**Verification result:** The patch management utility reported successful application of the Struts patch. However, the subsequent verification returned `Struts patched: False`. The patch status therefore requires further investigation before remediation can be confirmed.

### 2.2 Network Segmentation Controls

**Control:** Network Segmentation  
**Control ID:** CTL-005  
**Related Policy:** POL-001  
**Responsible Role:** Network Engineer

The network segmentation implementation was invoked to simulate the introduction of network access restrictions between systems. The objective was to reduce unnecessary connectivity and restrict access to sensitive resources according to the principle of least privilege.

Effective network segmentation should limit direct access to the database server to authorised systems and services, reducing the potential for an attacker to move laterally after compromising an internet-facing application.

**Verification result:** The patch management utility reported that the network segmentation rules were applied successfully. However, the verification returned `Network segmented: False`. Additional testing is required to establish whether the simulated network restrictions are correctly reflected in the patch status and whether the intended traffic restrictions are effective.

### 2.3 Database Security Controls

**Control:** Database Security  
**Control ID:** CTL-006  
**Related Policy:** POL-001  
**Responsible Role:** Database Administrator

The database security configuration was invoked to simulate stronger authentication and access controls for the MySQL database server. The intended improvements include restricting database access to authorised users and applications, removing insecure default credentials, and limiting unnecessary privileges.

These measures are intended to reduce the risk of unauthorised access to sensitive customer information.

**Verification result:** The verification process returned `MySQL secured: True`. This confirms that the corresponding status flag was set in the simulation. Further technical testing would be required to confirm the actual effectiveness of authentication and database access restrictions.

### 2.4 Security Monitoring Controls

**Control:** Real-time Security Monitoring  
**Control ID:** CTL-007  
**Responsible Role:** Security Engineer

A monitoring script was created at `monitoring/security_monitor.sh`. The script is intended to examine selected web server logs for suspicious multipart HTTP requests, review database process information, identify recently modified web application files, and record alerts when specified conditions are detected.

A cron configuration file was also created at `monitoring/security_cron` to represent the proposed five-minute monitoring schedule.

A security monitoring coverage metric was added to the governance tracker to support measurement of monitoring coverage across critical systems.

**Verification result:** The verification process confirmed that the monitoring script exists. However, the presence of the script and cron configuration file does not establish that scheduled execution, log collection, alert delivery, or monitoring coverage is operational. These functions require additional testing.

### 2.5 Governance Oversight Controls

**Policy:** Security Governance Oversight  
**Policy ID:** POL-004  
**Control:** Executive Security Oversight  
**Control ID:** CTL-008  
**Responsible Role:** Chief Executive Officer

The file `governance_oversight.md` was created to document proposed security governance responsibilities and oversight arrangements.

The document defines responsibilities for executive leadership and security management, establishes proposed reporting and escalation arrangements, and identifies quarterly security briefings, annual programme reviews, and board-level security oversight as governance activities.

The associated policy and control were added to the governance tracker to establish accountability and support future governance reviews.

**Verification result:** The verification process confirmed that the governance oversight document exists and that the governance tracker contains the newly recorded policy and control. The actual operation of executive reporting, board reviews, and escalation arrangements has not yet been demonstrated.

## 3. Governance Tracker Summary

The verification process reported the following tracker totals after implementation:

| Governance item | Total recorded |
|---|---:|
| Policies | 4 |
| Controls | 8 |
| Metrics | 5 |

These totals indicate that the implementation script updated the governance tracker. They do not independently demonstrate that every recorded control is operating effectively.

## 4. Vulnerability Scan Results

The vulnerability scanner completed its execution and saved a report to:

`vulnerability_report_20261011_012206.json`

The terminal summary reported:

| Severity | Reported count |
|---|---:|
| Critical | 0 |
| High | 0 |
| Medium | 1 |
| Low | 0 |
| Unknown | 1 |

The scanner also reported three vulnerabilities in total. The displayed severity counts account for only two findings, so the detailed JSON report must be reviewed to identify and classify the remaining finding.

The scan completed successfully as a process, but the presence of findings means that remediation cannot be declared complete based on this result alone. The outstanding findings should be reviewed, prioritised, assigned to responsible owners, and retested after remediation.

## 5. Verification Summary

The implementation and verification process produced the following results:

| Verification item | Result |
|---|---|
| Struts patch status | Not confirmed; returned False |
| MySQL security status | Status flag returned True |
| Network segmentation status | Not confirmed; returned False |
| Monitoring script | File existence confirmed |
| Governance oversight document | File existence confirmed |
| Governance tracker update | Confirmed; 4 policies, 8 controls, 5 metrics |
| Vulnerability scan | Completed; findings remain |
| Attack simulation | Requires separate execution and documented results |

The results distinguish between controls that were recorded, status flags that were checked, and controls whose technical effectiveness still requires validation.

## 6. Recommendations

The following actions are recommended:

1. Investigate the Struts patch status discrepancy and confirm that the simulated vulnerability has been remediated.
2. Investigate the network segmentation status and test the intended restrictions between the web and database servers.
3. Validate MySQL authentication, account privileges, and permitted network access rather than relying solely on the status flag.
4. Test the monitoring script, confirm that its dependencies and log paths are valid, and verify that scheduled execution and alert generation work as intended.
5. Review the complete vulnerability scan report, reconcile the reported total with the severity breakdown, and document remediation and retesting.
6. Execute the authorised attack simulation again and retain the output as evidence of whether the simulated attack succeeds or fails.
7. Establish periodic reporting of patch compliance, monitoring coverage, unresolved vulnerabilities, and remediation progress to the appropriate management and governance stakeholders.

## 7. Conclusion

The security governance control implementation exercise established records for patch management, network segmentation, database security, security monitoring, and executive oversight. It also updated the governance tracker and completed a vulnerability scan.

The verification results indicate that further work is necessary before all controls can be considered effective. In particular, the Struts patch and network segmentation status checks returned False, while the vulnerability scan reported outstanding findings. Completing the recommended validation and remediation activities will provide stronger evidence that the controls address the identified technical and governance weaknesses and reduce the risk of a breach similar to the Equifax incident.



# Security Governance Dashboard User Guide

## 1. Introduction

This user guide explains how to access, navigate and interpret the Security Governance Executive Dashboard developed for the ICDFA GRC102 security governance laboratory.

The dashboard presents key security metrics, risk information, compliance indicators and historical trends. It is designed to help management and other authorised stakeholders understand the organisation's security posture, identify areas requiring attention and support informed governance decisions.

The dashboard uses simulated laboratory data. Its figures demonstrate how security performance can be reported and should not be interpreted as verified evidence of a real organisation's security posture.

## 2. Dashboard Requirements

The following are required to use the dashboard:

- The generated `executive_dashboard.html` file.
- A modern web browser, such as Firefox or Chromium.
- The `metrics_visualizations` directory containing the five generated chart images.
- The Python metrics script and its required dependencies to regenerate the dashboard.

Keep the HTML file and its visualisation directory in their original relative locations. Moving the HTML file without the chart directory may cause the charts not to display correctly.

## 3. Accessing the Dashboard

### Step 1: Open the laboratory directory

Open a terminal and enter:

    cd ~/security_governance_lab

### Step 2: Generate the dashboard

If the dashboard has not yet been generated, run:

    python3 governance_metrics.py

The script should generate the executive dashboard, board report and five visualisation images.

### Step 3: Open the dashboard

Run:

    xdg-open executive_dashboard.html

Alternatively, open the laboratory directory in the file manager and double-click `executive_dashboard.html`.

The dashboard should open in your default web browser.

## 4. Dashboard Sections

### 4.1 Security Posture Summary

This section presents the key security performance indicators:

- Patch Compliance: Percentage of in-scope systems meeting patching requirements.
- Vulnerability Remediation Time: Average time taken to remediate identified vulnerabilities.
- Security Incidents: Number of recorded incidents during the reporting period.
- Security Monitoring Coverage: Percentage of critical systems covered by security monitoring.
- Policy Compliance: Percentage of assessed policy requirements meeting defined standards.

The displayed figures should be compared with their respective targets. A favourable result in one metric does not establish that the entire security programme is effective.

### 4.2 Risk Summary

The risk summary displays the number of risks classified as critical, high, medium and low. It also presents the risk acceptance rate and average risk remediation time.

Management should review significant risks, confirm that mitigation plans have assigned owners and due dates, and ensure that risk acceptance follows the approved authorisation process.

### 4.3 Compliance Summary

This section presents policy compliance, control effectiveness, open audit findings, regulatory compliance, security training completion and third-party risk assessment indicators.

These indicators can help identify areas that require further investigation. Reported compliance percentages should be supported by appropriate records and assessment evidence before being used for formal assurance.

### 4.4 Trend Visualisations

The dashboard contains five charts:

1. Patch Compliance Trend: Tracks patch compliance over six monthly periods.
2. Vulnerability Remediation Time Trend: Shows changes in average remediation time.
3. Security Incidents Trend: Displays the number of incidents recorded in each period.
4. Security Monitoring Coverage Trend: Tracks the proportion of critical systems covered by monitoring.
5. Policy Compliance Trend: Shows changes in assessed policy compliance.

The charts include target lines to support comparisons between performance and expected outcomes.

### 4.5 Key Recommendations

The recommendations section highlights suggested actions, including maintaining patch management processes, addressing new vulnerabilities, conducting security awareness training, performing periodic security assessments and reviewing security policies.

Recommendations should be prioritised according to risk, assigned to responsible owners and tracked until completion.

## 5. Interpreting Metric Status

The dashboard uses green, amber and red indicators to communicate performance:

- Green: The metric meets or exceeds its approved target.
- Amber: The metric requires attention or is approaching an escalation threshold.
- Red: The metric is materially outside its approved target and may require urgent action.

In this laboratory dashboard, some status indicators are predefined in the HTML. They do not automatically evaluate every metric against its target. Users should therefore verify the displayed values and supporting evidence rather than relying on colour alone.

For metrics where lower values are better, such as remediation time, a value below the target is generally favourable. For metrics where higher values are better, such as patch compliance, the value should meet or exceed the minimum target.

A reported zero security incidents should not automatically be interpreted as proof of security. Monitoring coverage, incident reporting quality and other control evidence must also be considered.

## 6. Using the Dashboard for Governance Decisions

The dashboard supports governance oversight in the following ways:

1. Identifying performance gaps by comparing current metrics with approved targets.
2. Monitoring historical trends to assess whether performance is improving or deteriorating.
3. Supporting risk prioritisation and the allocation of security resources.
4. Highlighting areas requiring further investigation or control testing.
5. Supporting discussions between technical teams, management and the board.
6. Tracking recommendations and encouraging accountability for remediation actions.

The dashboard should be used alongside the board report, risk register, audit findings and other supporting evidence.

## 7. Refreshing the Dashboard

The laboratory script generates a new set of simulated historical values whenever it runs.

To refresh the dashboard:

1. Open the laboratory directory.
2. Run `python3 governance_metrics.py`.
3. Wait for the script to finish.
4. Reopen or refresh `executive_dashboard.html` in the browser.
5. Review the generated board report and charts.

Because the script uses random historical values, the figures may differ between executions. A production implementation should obtain validated data from operational systems and maintain appropriate records of reporting periods and historical results.

## 8. Troubleshooting

### Dashboard does not open

Confirm that the file exists:

    ls -l executive_dashboard.html

If it is missing, run the metrics script again and review any errors.

### Charts do not appear

Confirm that the chart files exist:

    ls -l metrics_visualizations/

Ensure the HTML file and `metrics_visualizations` directory remain in the expected relative locations.

### Python reports a missing module

Install the required Matplotlib package using the package manager available in your Kali Linux environment, or follow your laboratory's Python dependency instructions.

### Dashboard values change unexpectedly

The supplied script generates random historical data. Re-running it can produce different values. These are simulated results, not live measurements.

## 9. Reporting and Maintenance

The dashboard should be reviewed at the agreed reporting frequency. Metric owners should validate source data, investigate material deviations, record corrective actions and escalate significant risks through approved governance channels.

The dashboard layout, metric definitions and targets should be reviewed periodically to ensure that they remain relevant to the organisation's objectives, risk appetite and compliance obligations.

## 10. Conclusion

The Security Governance Executive Dashboard provides a consolidated view of security performance and helps stakeholders interpret key metrics, identify areas of concern and prioritise corrective actions.

When used alongside validated evidence, clear accountability and regular reporting, the dashboard can support effective security governance and continuous improvement. In this laboratory exercise, it demonstrates the reporting process using simulated data rather than confirming actual organisational performance.

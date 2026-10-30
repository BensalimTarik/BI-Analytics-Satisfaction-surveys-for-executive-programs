
# BI Project – General Satisfaction Surveys for Executive Programs

## 1. Project Overview

As part of the monitoring of teaching and training quality and performance within the C&D Group, this project aims to implement a structured satisfaction survey process for students enrolled in Executive programs.

This process is designed to measure and monitor student satisfaction across several analytical dimensions, including teaching quality, student support, information and guidance, logistics, and the perceived value of the training programs.

The objective is to provide a consolidated and actionable view of the student experience in order to identify key strengths, areas for improvement, and potential action plans.

## 2. Business Objectives

The project addresses six main objectives:

| ID | Specific Objective | Success Indicator | Target |
|---|---|---|---|
| O1 | Design and make available satisfaction survey forms based on the defined analytical dimensions. | Survey forms validated and available | 100% of required forms |
| O2 | Automate the distribution of survey forms to the relevant students according to defined rules and deadlines. | Automated questionnaire delivery rate | 100% of eligible students |
| O3 | Automate the collection and centralization of survey responses. | Rate of responses correctly received and recorded | ≥ 95% of submitted responses |
| O4 | Transform, clean, and prepare data from different sources for analytical use. | Rate of compliant and usable data | ≥ 95% of data usable |
| O5 | Implement interactive dashboards to monitor student satisfaction across the main analytical dimensions. | Operational dashboard and available indicators | 100% of priority indicators |
| O6 | Enable business and academic managers to identify trends, strengths, and areas for improvement based on survey results. | Availability of indicators and analyses required for decision-making | 100% of priority analytical needs covered |

## 3. Functional Scope and Business Process

| Process Step | Target Operating Model | Expected Improvements |
|---|---|---|
| **Data Collection and Preparation** | Implement automated processes to extract the required data from IGOR and transfer it to a dedicated SQL Server database. Introduce data quality checks and transformation rules to ensure data consistency before analytical use. | - Reduce manual operations in Excel.<br>- Improve the reliability and standardization of survey data.<br>- Facilitate periodic data refreshes and ensure process traceability. |
| **Survey Management and Distribution** | Develop HTML forms tailored to the needs of each school brand, with a unique identifier linking each response to the relevant survey and training period. Automate recipient preparation and questionnaire distribution according to defined rules. | - Reduce survey preparation and distribution time.<br>- Minimize data-entry errors and incorrect associations between forms and training periods.<br>- Improve survey and recipient traceability. |
| **Response Collection and Centralization** | Use Azure Logic Apps to automate response processing and storage in a dedicated database. Implement controls to validate responses, limit duplicates, and monitor processing errors. | - Eliminate manual copy-and-paste operations in Excel.<br>- Reduce handling errors.<br>- Centralize responses in an analytical data structure and ensure process monitoring. |
| **Analysis and Reporting** | Design detailed Power BI reports organized into multiple pages according to business requirements. Structure the data model using a star schema, with fact tables and dimensions suited to the analytical requirements. | - Improve KPI reliability and consistency.<br>- Address stakeholders' priority analytical needs.<br>- Facilitate satisfaction analysis by school brand, training program, cohort, and evaluation dimension.<br>- Optimize refresh performance and simplify report maintenance. |

## 4. Key Performance Indicators (KPIs)

The dashboards are designed to monitor the following indicators:

| KPI | Definition | Formula / Rule | Source | Frequency | Target | Requirement |
|---|---|---|---|---|---|---|
| **KPI 01 – Number of Responses Received** | Number of responses recorded for a survey campaign. | Count of valid responses received, according to the defined deduplication rules. | Responses database | At each BI refresh | Ongoing monitoring | BR-05 |
| **KPI 02 – Response Rate** | Proportion of invited students who responded to the survey. | (Number of students who responded ÷ Number of students invited) × 100 | Responses database and invitations database | At each BI refresh | ≥ 70% as an indicative target | BR-05 |
| **KPI 03 – Number of Notifications Sent** | Total number of invitations and reminders sent to students. | Count of notifications sent, by type and campaign. | Notification history | At each BI refresh | 100% of planned notifications processed | BR-05 |

## 5. Data Architecture and Sources

### 5.1. Data Sources

**Source 1 – IGOR / SQL Server**

Data includes, in particular:
- Student registrations and student information.
- Training programs.
- Analytical dimensions.
- Current academic year.

Access to this data is read-only and subject to the permissions granted.

**Source 2 – Dedicated Data Analytics SQL Server Database**

This database contains structured and prepared data used for processing and analysis.

Read and write operations are controlled according to process requirements.

### 5.2. Technologies Used

- **IGOR:** Source data system.
- **SQL Server:** Data storage and centralization.
- **Azure Logic Apps:** Process automation and survey response collection.
- **HTML:** Questionnaire design.
- **Power BI:** Data modeling, analysis, and visualization.

## 6. Business Rules and Data Quality

| ID | Rule | Details / Example | Validated By |
|---|---|---|---|
| **RG-01** | KPI Definition and Calculation | Each KPI must have a documented business definition, calculation formula, scope, and filtering rules. Formulas must be consistent with the "Indicators and KPIs" section and validated before implementation in Power BI. | School Brand Directors, Academic Managers |
| **RG-02** | Survey Process Automation | The process is organized into three separate Azure Logic Apps workflows: 1. Sending questionnaires to the relevant recipients; 2. Notifying and sending reminders to students who have not responded, according to defined rules; 3. Receiving and centralizing responses in the dedicated database. Each workflow must ensure process traceability and error handling. | School Brand Directors, Academic Managers |
| **RG-03** | Matching Surveys with Recipients | Each survey must be associated with the training period (PF), training program, school brand, and relevant learner group. Matching must rely on reliable identifiers from reference data. Any missing or ambiguous association must be flagged before distribution. | School Brand Directors, Academic Managers |
| **RG-04** | Response and Duplicate Management | Each response must be linked to an identifiable survey. Rules regarding multiple responses, repeated submissions, and the treatment of the latest response must be defined before KPI calculations. | School Brand Directors, Academic Managers |
| **RG-05** | Reminder Management | A reminder is triggered only for eligible recipients who have not responded to the relevant survey, subject to the defined reminder limit. The sending and response statuses must be recorded. | School Brand Directors, Academic Managers |
| **RG-06** | Access to Results | Users can access results within their scope of responsibility, according to the permissions granted. Individual responses and comments are accessible only to authorized users. | School Brand Directors, Academic Managers |

---

*Project carried out as part of the student satisfaction analysis initiative for the Compétences & Développement Group.*

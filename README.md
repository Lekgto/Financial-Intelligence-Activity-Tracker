# Financial-Intelligence-Activity-Tracker
The Financial Intelligence Activity Tracker (FIAT) is a Proof of Concept (PoC) developed by Kananelo Lekgetho to address the technical and psychological barriers to effective personal investment management. The project transitions from fragmented, manual data tracking to an automated, centralized Business Intelligence (BI) solution.

Technical Manual Layout
Chapter 1: Introduction
This section establishes the "why" behind the project, moving from a personal pain point to a structured technical objective.

Context: The author identified a problem with fragmented financial data across platforms like EasyEquities and Capitec.
Problem Statement: Data silos and inconsistent formats made longitudinal analysis (tracking performance over years) and behavioral insight detection impossible.
Objectives: The primary goal was to implement a data warehouse MVP with an automated ETL pipeline to transform semi-structured data (emails, PDFs) into a queryable format.
Solution & Scope: FIAT is defined as a pipeline utilizing SQL Server Integration Services (SSIS) for staging and a Star Schema with a fact constellation for storage. Its scope is restricted to personal Gmail and manual statement data.
Limitations: The author identifies "incompleteness" as a major risk, as some source reports (like transaction histories) only allow for a one-year lookback.


Chapter 2: Existing Systems and Foundational Literature
A dual-purpose section that critiques current tools while grounding the project in academic theory.

Critique of Current Systems:
Capitec: While it offers monthly bar charts, it lacks continuous behavioral tracing and doesn't integrate external financial activity.
EasyEquities (EE): Provides advanced visual reporting (pie charts, line graphs) but suffers from a "limited time horizon" and high cognitive load due to dense numerical tables.

Theoretical Foundations:
Data Warehousing: References Inmon (2005) for definitions (subject-oriented, integrated, etc.) and Kimball & Ross (2013) for the dimensional modeling approach.
Business Intelligence (BI): Discusses the six architectural components of BI: ETL tools, data store, query/reporting, visualization, monitoring, and analytics.
Behavioral Finance: Integrates Prospect Theory (the "pain of losing" vs. "joy of gaining") and the Framing Effect, explaining how these psychological biases necessitate a system like FIAT to see patterns clearly.

Chapter 3: Requirements Analysis
This chapter translates the conceptual needs into specific data structures.

Process Mapping: Includes "As-Is" activity diagrams for investment, selling, and withdrawal processes to understand how data currently flows.
The Information Package: Defines the "Information Subject" as "Investment Account Activity Analysis".
Data Structures: The author defines early versions of the Measures Table (quantitative values), Dimension Table (descriptive context), and Attributes Table.

Chapter 4: Architectural Design
The blueprint of the proposed solution.
Functional Requirements: Outlines what the system must do, such as consolidating sources and providing interactive investigation environments.
To-Be Process: Uses an activity diagram to show how the proposed system replaces manual consolidation with an automated pipeline.
Dimensional Model: Details a Fact Constellation Schema, which is essential for handling multiple business processes (like buying and selling) within one warehouse.
Tool Justification: Provides rationales for choosing Python (flexibility), SSIS (enterprise-grade ETL), SQL Server (storage), and Metabase (visualization) over alternatives.

Chapter 5: Implementation
The technical execution of the design.

Layered ETL Approach:
Layer 1 (Python): Uses the Gmail API, BeautifulSoup, and pandas to extract unstructured email content and convert it into CSV files.
Layer 2 (SSIS): Orchestrates the movement of CSV data into the SQL data mart using modular packages for dimensions and facts.
SQL Process Logic: Explains specific queries used for data cleaning, such as:
Date Dimension Derivation: Extracting year, quarter, and month from transaction dates.
Normalisation: Consolidating related entries into single events and separating principal amounts from fees.
Currency Conversion: Standardizing USD transactions into local currency using fixed exchange rates.
Information Delivery: Demonstrates the final output via Metabase, including dashboards for "Top 10 Most Profitable Entities" and "Assets Bought but Never Sold".


Appendices
Appendix A: Discloses the exact prompts used with Google Gemini AI to generate the initial Python extraction scripts.
Appendices B & C: Provide technical setup guides for Metabase, SQL Server, and Visual Studio.

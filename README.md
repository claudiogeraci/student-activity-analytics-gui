# student-activity-analytics-gui

Python and Tkinter desktop prototype for chunked JSON data processing, student engagement analytics, data visualisations (Matplotlib and Seaborn), and ethical software engineering documentation.

## Overview

This prototype application provides a desktop interface built with Python and Tkinter to load, clean, transform, and visualise student activity and engagement data. It pairs guided user controls and feedback mechanisms with chunked JSON data handling to prevent interface freezes and support data analysis.

## GUI Design and User Interaction

* **Core Controls and Layout:** Uses a top-to-bottom workflow and grid layout to place controls clearly for prototype navigation. Key actions include **Load initial data set**, **Remove system and folder outputs**, and **Rename columns in `activity_log` and `user_log`**.
* **Confirmation Prompts:** Displays a confirmation prompt after a button click to verify user intent, protect data integrity, and prevent accidental data loads or modifications.
* **Immediate Output Feedback:** Updates output labels immediately after each action to confirm results, build user confidence, and avoid repeated clicks caused by missing feedback (similar to deletion feedback in spreadsheet tools).
* **Proposed Future Enhancements:**
  * Add check buttons (`Checkbutton`) after outputs so users can tick off completed steps in a sequential data-manipulation workflow.
  * Add a comment or text-editor feature after actions to record and save notes on specific findings, especially in statistics and correlation views.

## Data Format and Chunking Strategy

* **Why JSON Over XML:** Uses JSON for its lightweight structure, smaller file sizes, and built-in Python support. Processing large CSV files in smaller JSON chunks prevented the application from freezing during testing.
* **Comparison with XML:** A hierarchical XML structure would require heavier parsing and additional manipulation for removal and reshaping tasks compared to loading JSON into pandas DataFrames. XML's DOM or SAX parsers suit small-to-medium files, and could fit small inputs such as `component_codes`, though error handling caught a JSON load issue on `component_codes` and fell back to building a small DataFrame directly.

## Data Cleaning, Aggregation, and Visualisation

* **Data Preparation and Cleaning:** Splits large datasets into chunks before analysis, filters records to target components (*Quiz*, *Lecture*, *Assignment*, *Attendance*, and *Survey*), checks required columns (`User_ID`, `Component`, `Month_Year`, and interaction counts) while assigning missing columns or values safely (such as `None` for missing columns or `0` for missing components), and converts `Month_Year` to strings to avoid datetime grouping and formatting issues.
* **Reshaping and Libraries:** Uses `pandas` for DataFrame manipulation, merging, filtering, and pivot tables (`User_ID` as index, `Component` as columns, and interaction counts as values with missing entries filled as `0`), rather than relying on `NumPy` alone. Embeds `Matplotlib` bar charts and `Seaborn` correlation heatmaps inside Tkinter.
* **Key Prototype Insights:** Across the 13-week semester, activity peaked in **November** across *Assignment*, *Quiz*, *Lecture*, and *Survey*, while *Attendance* remained at zero. **User 129** showed the highest overall engagement across examined components, with higher engagement on assignments, courses, and quizzes than on book and project components—offering useful signals for planning student learning support.

## Ethics, Professionalism, and Governance

* **Foundations and Standards:** Distinguishes morality, ethics, and law, and highlights core professional values—commitment, integrity, responsibility, and accountability—alongside SWEBOK pillars (knowledge, professional society membership, and a code of ethics) and relevant legislation such as the Data Protection Act, Human Rights Act 1998, Computer Misuse Act 1990, and Digital Economy Act 2017.
* **Ethically Driven Software Development (EDSD):** Applies EDSD principles to bridge technical execution with ethical responsibility, evaluate grey areas across the software lifecycle, and reduce risks of software failure, harm, or legal liability.

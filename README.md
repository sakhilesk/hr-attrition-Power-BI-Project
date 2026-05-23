<div align="center">
  <h1>Executive HR Analytics: Diagnostic Attrition Tracking Dashboard</h1>
  <p><strong>An End-to-End Power BI Portfolio Project isolating workforce turnover mechanics and operational burnout drivers.</strong></p>
  
  <p>
    <a href="#1-the-strategic-business-problem">Business Problem</a> •
    <a href="#2-data-engineering--etl-transformations">Data Engineering</a> •
    <a href="#3-analytical-modeling-architecture">Data Model</a> •
    <a href="#4-custom-analytical-logic-dax">DAX Formulas</a> •
    <a href="#5-key-business-insights">Insights & Impact</a>
  </p>
</div>

<hr />

<h2>📌 1. The Strategic Business Problem</h2>
<p>
  High employee turnover introduces significant hidden operational liabilities, including inflated replacement recruiting costs, severed client continuity, and structural friction in departmental performance. 
</p>
<p>
  The HR Leadership team lacked centralized data mechanisms to diagnose patterns behind ongoing staff departures. The primary objective of this project was to transform static, disconnected workforce records into a single, comprehensive dynamic tracking canvas to answer three critical operational questions:
</p>
<ul>
  <li><strong>Where</strong> is attrition structurally concentrated across roles and business units?</li>
  <li><strong>Who</strong> is leaving in terms of tenure brackets and experiential demographics?</li>
  <li><strong>Why</strong> are they exiting—is churn driven by compensation gaps, performance friction, or systemic operational burnout?</li>
</ul>

<hr />

<h2>⚙️ 2. Data Engineering & ETL Transformations</h2>
<p>
  The raw organizational records consisted of 1,470 employee snapshots across 35 distinct attributes. Before modeling, structural cleanup was required in <strong>Power Query</strong> to ensure data integrity and optimize processing speeds:
</p>
<ul>
  <li><strong>Elimination of Non-Informational Bulk:</strong> Dropped low-variance columns where every single row contained matching data (<code>EmployeeCount = 1</code>, <code>Over18 = Y</code>, <code>StandardHours = 80</code>), lowering the data model file size and memory footprint.</li>
  <li><strong>Strict Schema Type Optimization:</strong> Explicitly mapped categorical fields to descriptive strings and converted financial values (<code>MonthlyIncome</code>, <code>DailyRate</code>) to fixed decimal structures for optimized rendering performance.</li>
  <li><strong>Granular Analytical Binning:</strong> Built custom conditional columns to segment continuous scales into distinct descriptive brackets for strategic group evaluation (e.g., custom age groups, travel status, and mileage buckets).</li>
</ul>

<hr />

<h2>🏗️ 3. Analytical Modeling Architecture</h2>
<p>
  To support clean execution and efficient querying, the data is organized around a clean operational structure in the <strong>Model View</strong>:
</p>
<ul>
  <li>Developed an explicit, isolated <strong>Date Dimensions Calendar Table</strong> via custom DAX to manage global timeline slices.</li>
  <li>Set up a dedicated, isolated measures repository table (<code>_All Measures</code>) to consolidate calculated logic, ensuring the schema remains production-ready, clean, and easily maintainable.</li>
</ul>

<hr />

<h2>🧮 4. Custom Analytical Logic (DAX Formulas)</h2>
<p>Rather than relying on basic automated aggregations, the dashboard uses targeted business metrics to track performance across different groups:</p>

<pre><code><strong>Workforce Churn Foundation:</strong>
Attrition Rate = 
DIVIDE(
    CALCULATE(COUNT(HR_Data[EmployeeNumber]), HR_Data[Attrition] = "Yes"),
    COUNT(HR_Data[EmployeeNumber]), 
    0
)
</code></pre>

<pre><code><strong>Burnout Correlation Diagnostic:</strong>
Burnout Attrition Rate = 
CALCULATE(
    [Attrition Rate], 
    HR_Data[OverTime] = "Yes"
)
</code></pre>

<hr />

<h2>💡 5. Key Business Insights Identified</h2>

<table>
  <thead>
    <tr>
      <th>Operational Metric</th>
      <th>Data Observation</th>
      <th>Strategic Root Cause Identified</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>The Burnout Factor</strong></td>
      <td>Personnel assigned to Overtime experience an <strong>Attrition Rate of over 30%</strong>.</td>
      <td>This is nearly triple the rate of standard shift personnel, directly connecting extended hours to lower retention.</td>
    </tr>
    <tr>
      <td><strong>High-Risk Roles</strong></td>
      <td><strong>Laboratory Technicians</strong> and <strong>Sales Representatives</strong> exhibit the highest overall organizational churn.</td>
      <td>Signals structural stress points, onboarding friction, or uncompetitive base-pay scales for entry-level tasks.</td>
    </tr>
    <tr>
      <td><strong>Tenure Friction</strong></td>
      <td>Staff turnover is heavily concentrated within the <strong>0–2 Year tenure bracket</strong>.</td>
      <td>Highlights a critical breakdown during the initial employee integration and onboarding phase.</td>
    </tr>
  </tbody>
</table>

<hr />

<h2>🚀 6. Strategic Operational Recommendations</h2>
<ol>
  <li><strong>Implement Overtime Threshold Safeguards:</strong> Create automated alerts when an individual's consecutive monthly overtime exceeds structural limits to actively reduce burnout in high-attrition teams.</li>
  <li><strong>Review Entry-Level Compensation:</strong> Conduct a market-rate salary benchmark review for <em>Laboratory Technicians</em> to ensure compensation lines up with competitive standards.</li>
  <li><strong>Launch a First-Year Mentorship Initiative:</strong> Build target check-ins into the onboarding program for employees in their first 24 months to help improve long-term retention.</li>
</ol>

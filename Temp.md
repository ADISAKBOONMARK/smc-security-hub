# Template

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>SolJu</title>
    <style>
      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        margin: 20px;
        line-height: 1.6;
        background-color: #f4f7fa;
        color: #333;
      }
      h1,
      h2,
      h3 {
        color: #2c3e50;
      }
      h1 {
        border-bottom: 2px solid #3498db;
        padding-bottom: 10px;
      }
      .vulnerability {
        border: 1px solid #ddd;
        padding: 15px;
        margin-bottom: 20px;
        border-radius: 8px;
        background-color: #ffffff;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      }
      .code {
        background-color: #f9f9f9;
        padding: 10px;
        margin: 10px 0;
        overflow-x: auto;
        font-family: "Courier New", Courier, monospace;
        font-size: 0.95em;
        position: relative;
      }
      .line-numbers {
        position: absolute;
        left: 0;
        width: 30px;
        border-right: 1px solid #ddd;
        text-align: right;
        padding-right: 10px;
        user-select: none;
        color: #888;
      }
      .line-numbers span {
        display: block;
        height: 20px;
      }
      .suggestion {
        background-color: #e8f5e9;
        border-left: 5px solid #4caf50;
        padding: 10px;
        margin: 10px 0;
      }
      .issue {
        background-color: #fff3e0;
        border-left: 5px solid #ff9800;
        padding: 10px;
        margin: 10px 0;
      }
      pre {
        margin: 0;
        padding-left: 40px; /* Adjust for line numbers */
      }
      p {
        margin: 0 0 10px;
      }
      code {
        background-color: #e8e8e8;
        padding: 2px 4px;
        border-radius: 4px;
        font-size: 0.95em;
      }
      .audit-files {
        border-radius: 8px;
        margin-top: 20px;
        border-collapse: collapse;
        width: 100%;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      }
      .audit-files th,
      .audit-files td {
        border: 1px solid #ddd;
        padding: 8px;
        text-align: left;
      }
      .audit-files th {
        background-color: #3498db;
        color: white;
      }
      .audit-files tr:nth-child(even) {
        background-color: #f2f2f2;
      }
      .audit-files tr:hover {
        background-color: #ddd;
      }
      .severity-matrix {
        margin: 20px 0;
        overflow-x: auto;
      }
      .severity-matrix table {
        width: 100%;
        border-collapse: collapse;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        border-radius: 8px;
        overflow: hidden;
      }
      .severity-matrix th,
      .severity-matrix td {
        padding: 12px 15px;
        text-align: left;
        border: 1px solid #e0e0e0;
      }
      .severity-matrix th {
        background-color: #3498db;
        color: white;
        font-weight: bold;
      }
      .severity-matrix tr:nth-child(even) {
        background-color: #f8f9fa;
      }
      .severity-matrix tr:hover {
        background-color: #f1f1f1;
      }
      .severity {
        font-weight: bold;
        padding: 3px 8px;
        border-radius: 4px;
        display: inline-block;
        margin-right: 8px;
      }
      .severity-high {
        background-color: #ffcdd2;
        color: #c62828;
      }
      .severity-medium {
        background-color: #fff9c4;
        color: #f57f17;
      }
      .severity-low {
        background-color: #dcedc8;
        color: #33691e;
      }
      .severity-info {
        background-color: #e3f2fd;
        color: #0d47a1;
      }
      .risk-high {
        background-color: #ffcdd2;
        color: #c62828;
      }
      .risk-med-hi {
        background-color: #ffcdd2;
        color: #c62828;
      }
      .risk-medium {
        background-color: #fff9c4;
        color: #f57f17;
      }
      .risk-med-low {
        background-color: #fff9c4;
        color: #f57f17;
      }
      .risk-low {
        background-color: #dcedc8;
        color: #33691e;
      }
    </style>
  </head>
  <body>
    <h1>{{REPORT_TITLE}}</h1>
    <h2>Overview</h2>
    <p>{{OVERVIEW_TEXT}}</p>

    <h2>Audit Files</h2>
    <table class="audit-files">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Location</th>
        </tr>
      </thead>
      <tbody>
        {{AUDIT_FILES_TABLE_ROWS}}
        <!-- <tr>
                <td>[ID]</td>
                <td>[NAME]</td>
                <td>[LOCATION]</td>
            </tr> -->
      </tbody>
    </table>

    <h2>Risk Matrix</h2>
    <p>
      The risk assessment for each finding is determined by combining the
      likelihood of exploitation with the potential severity of impact. This
      matrix helps prioritize remediation efforts based on overall risk to the
      system.
    </p>
    <div class="severity-matrix">
      <table>
        <thead>
          <tr>
            <th>Likelihood \ Severity</th>
            <th>Negligible</th>
            <th>Minor</th>
            <th>Moderate</th>
            <th>Significant</th>
            <th>Severe</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><strong>Very Likely</strong></td>
            <td class="risk-med-low">Med Low</td>
            <td class="risk-medium">Medium</td>
            <td class="risk-med-hi">Med Hi</td>
            <td class="risk-high">High</td>
            <td class="risk-high">High</td>
          </tr>
          <tr>
            <td><strong>Likely</strong></td>
            <td class="risk-med-low">Med Low</td>
            <td class="risk-medium">Medium</td>
            <td class="risk-med-hi">Med Hi</td>
            <td class="risk-high">High</td>
            <td class="risk-high">High</td>
          </tr>
          <tr>
            <td><strong>Possible</strong></td>
            <td class="risk-low">Low</td>
            <td class="risk-med-low">Med Low</td>
            <td class="risk-medium">Medium</td>
            <td class="risk-med-hi">Med Hi</td>
            <td class="risk-high">High</td>
          </tr>
          <tr>
            <td><strong>Unlikely</strong></td>
            <td class="risk-low">Low</td>
            <td class="risk-low">Low</td>
            <td class="risk-med-low">Med Low</td>
            <td class="risk-medium">Medium</td>
            <td class="risk-med-hi">Med Hi</td>
          </tr>
          <tr>
            <td><strong>Very Unlikely</strong></td>
            <td class="risk-low">Low</td>
            <td class="risk-low">Low</td>
            <td class="risk-low">Low</td>
            <td class="risk-med-low">Med Low</td>
            <td class="risk-medium">Medium</td>
          </tr>
        </tbody>
      </table>
    </div>
    <p>
      When determining the risk level of a vulnerability, both the technical
      aspects of the issue and its potential business impact are considered.
    </p>

    <h2>Severity Matrix</h2>
    <div class="severity-matrix">
      <table>
        <thead>
          <tr>
            <th>Severity Level</th>
            <th>Description</th>
            <th>Impact</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="severity severity-high">HIGH</span></td>
            <td>
              Critical vulnerabilities that could lead to significant fund loss,
              contract compromise, or render core functionality unusable.
            </td>
            <td>
              Immediate risk to user funds, contract integrity, or system
              availability. Requires urgent remediation.
            </td>
          </tr>
          <tr>
            <td><span class="severity severity-medium">MEDIUM</span></td>
            <td>
              Vulnerabilities that could impact contract functionality under
              specific conditions or pose moderate risks to security.
            </td>
            <td>
              Significant but contained impact on specific operations,
              potentially affecting some users or transactions under particular
              circumstances.
            </td>
          </tr>
          <tr>
            <td><span class="severity severity-low">LOW</span></td>
            <td>
              Issues that represent minor risks or deviations from best
              practices but don't directly compromise security.
            </td>
            <td>
              Limited impact on contract functionality with minimal risk to user
              funds or operations.
            </td>
          </tr>
          <tr>
            <td><span class="severity severity-info">INFO</span></td>
            <td>
              Observations, code style issues, or informational findings that
              don't pose direct security risks.
            </td>
            <td>
              No immediate security impact, but may help improve code quality,
              gas efficiency, or maintainability.
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <h2>Vulnerabilities</h2>

    {{VULNERABILITIES_LIST}}
    <!-- <div class="vulnerability">
        <h3><span class="severity severity-[LEVEL]">[LEVEL]</span>[NUMBER]. [TITLE] ([STANDARD])</h3>
        <p><strong>Location:</strong> [FILE_PATH] (Lines [START]-[END])</p>
        <div class="issue">
            <p><strong>Vulnerability:</strong> [VULNERABILITY_DESCRIPTION]</p>
            <div class="code" data-lineStartAt="[LINE_NUMBER]">
                <div class="line-numbers"></div>
                <pre>[VULNERABLE_CODE]</pre>
            </div>
        </div>
        <div class="suggestion">
            <p><strong>Recommendation:</strong> [RECOMMENDATION_TEXT]</p>
            <div class="code" data-lineStartAt="[LINE_NUMBER]">
                <div class="line-numbers"></div>
                <pre>[RECOMMENDED_CODE]</pre>
            </div>
        </div>
    </div> -->

    <h2>Conclusion</h2>
    <p>{{CONCLUSION_TEXT}}</p>

    <p>Key recommendations include:</p>
    <ul>
      {{RECOMMENDATION_LIST_ITEMS}}
      <!-- <li>[RECOMMENDATION_TEXT]</li> -->
    </ul>

    <script>
      document.addEventListener("DOMContentLoaded", function () {
        document.querySelectorAll(".code").forEach(function (codeBlock) {
          const lineStart =
            parseInt(codeBlock.getAttribute("data-lineStartAt"), 10) || 1;
          const lines = codeBlock
            .querySelector("pre")
            .innerText.split("\n").length;
          const lineNumbers = codeBlock.querySelector(".line-numbers");
          lineNumbers.innerHTML = Array.from(
            { length: lines },
            (_, i) => `<span>${i + lineStart}</span>`
          ).join("");
        });
      });
    </script>
  </body>
</html>
```

# Main Template Variables

| **Property**                    | **Description**                                          |
| ------------------------------- | -------------------------------------------------------- |
| `{{REPORT_TITLE}}`              | The title of the security audit report                   |
| `{{OVERVIEW_TEXT}}`             | Introduction text describing the audit scope and purpose |
| `{{AUDIT_FILES_TABLE_ROWS}}`    | HTML rows listing all files that were audited            |
| `{{VULNERABILITIES_LIST}}`      | Generated HTML containing all vulnerability entries      |
| `{{CONCLUSION_TEXT}}`           | Summary of the audit findings                            |
| `{{RECOMMENDATION_LIST_ITEMS}}` | Bullet points with key recommendations                   |

---

# For Audit Files Table

| **Property** | **Description**                      |
| ------------ | ------------------------------------ |
| `[ID]`       | Identifier for the audited file      |
| `[NAME]`     | Name of the audited file             |
| `[LOCATION]` | Path or location of the audited file |

# For Vulnerability Entries

| **Property**                  | **Description**                                       |
| ----------------------------- | ----------------------------------------------------- |
| `[LEVEL]`                     | Severity level (HIGH, MEDIUM, LOW, INFO)              |
| `[NUMBER]`                    | Sequential number of the vulnerability                |
| `[TITLE]`                     | Title or name of the vulnerability                    |
| `[STANDARD]`                  | Security standard or classification reference         |
| `[FILE_PATH]`                 | Path to the file containing the vulnerability         |
| `[START]`                     | Starting line number where the vulnerability is found |
| `[END]`                       | Ending line number where the vulnerability is found   |
| `[VULNERABILITY_DESCRIPTION]` | Detailed description of the vulnerability             |
| `[LINE_NUMBER]`               | Starting line number for code snippets                |
| `[VULNERABLE_CODE]`           | Code snippet showing the problematic code             |
| `[RECOMMENDATION_TEXT]`       | Text describing how to fix the vulnerability          |
| `[RECOMMENDED_CODE]`          | Code snippet showing the recommended fix              |

# For Recommendation List

| **Property**            | **Description**                       |
| ----------------------- | ------------------------------------- |
| `[RECOMMENDATION_TEXT]` | Individual recommendation in the list |

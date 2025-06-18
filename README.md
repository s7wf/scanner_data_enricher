Live Security Data Enrichment Dashboard 🛡️

🚀 The Problem
Security teams often receive raw data from vulnerability scanners like Rapid7 or Nessus. While this data is detailed, it lacks crucial context. To prioritize remediation, analysts need to answer questions like:

What is the official NVD severity for this CVE?

Who owns this IP address?

Is this IP known for malicious activity?

This tool bridges that gap by enriching the raw data and presenting it in a format that is both visually intuitive and ready for ingestion into other tools like Splunk.

✨ Features
Zero Installation: Runs entirely in the browser. No dependencies, no server, no setup needed. Just open the .html file.

Flexible Data Input: Comes with built-in sample data but allows you to drag-and-drop your own JSON files.

Live Enrichment Simulation: Demonstrates the process of enriching data with external context from sources like:

NVD: For official CVSS scores and severities.

WHOIS: For IP ownership information.

IP Geolocation: For geographic context.

AbuseIPDB: For IP reputation (optional).

Interactive Dashboard: Generates a clean dashboard with dynamic charts (powered by Chart.js) to visualize:

Vulnerability severities.

Top 10 most common vulnerabilities.

Top 10 most vulnerable assets.

Top 10 most attacked ports.

CSV Export: Exports the final, enriched data to a CSV file, perfectly formatted for ingestion into Splunk or any other SIEM/data analysis platform.

⚙️ How to Use
Download: Clone this repository or simply download the demo.html file.

Open: Open demo.html in any modern web browser (Chrome, Firefox, Edge, etc.).

Load Data (Optional): The app loads with embedded sample data. To use your own, simply drag and drop your JSON file onto the upload area.

Enrich: Click the "Start Enrichment" button to begin the process.

Analyze: View the interactive dashboard and download the results as a CSV file.

📄 Data Format
The application expects a JSON file with a specific structure. The key fields it looks for are assets, which is a list of objects, and vulnerabilities within each asset.

Here is an example of the expected input format:

{
  "assets": [
    {
      "ip_address": "198.51.100.24",
      "hostname": "webserver01.example.com",
      "os": "Linux Ubuntu 22.04",
      "vulnerabilities": [
        {
          "cve_id": "CVE-2023-4567",
          "title": "Apache HTTP Server Path Traversal",
          "description": "A path traversal vulnerability...",
          "cvss_base_score": 7.5,
          "port": 443,
          "protocol": "TCP"
        }
      ]
    }
  ]
}

The application will attempt to map the following keys:

Asset: ip_address, hostname, os

Vulnerability: cve_id, title, cvss_base_score, port, protocol, description

🛠️ Technologies Used
HTML5

Tailwind CSS: For modern, responsive styling.

JavaScript (ES6+): For all application logic.

Chart.js: For beautiful, interactive charts.

🌍 Adapting for Real-World Use
This demo uses simulated API calls (mockEnrichIpInfo, mockEnrichCveInfo) for a fast and reliable presentation. To use this in a production environment, you would replace the mock functions in the <script> tag with real fetch calls to the actual APIs (NVD, WHOIS, etc.).

📜 License
This project is open-source and available under the MIT License.

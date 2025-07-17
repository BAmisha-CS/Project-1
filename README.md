# Project-1
Web Application Vulnerability Scanner 

A Python-based web vulnerability scanner built to detect common web application vulnerabilities such as **Cross-Site Scripting (XSS)** and **SQL Injection (SQLi)**. Designed with a user-friendly Flask interface, this tool helps cybersecurity students and professionals assess target URLs for input-based vulnerabilities.

📌 Features
- 🔎 Crawls and identifies input forms and URLs
- 💉 Automatically injects test payloads for XSS, SQLi, etc.
- 🧠 Uses regex and pattern matching to analyze HTTP responses
- 🌐 Web-based interface built with Flask for easy scanning
- 📝 Logs detailed scan results with payloads, evidence, and severity
- 📁 Generates structured JSON reports for every scan

 📁 Project Structure
vuln_scanner/
│
├── main.py # Flask web interface
├── scanner.py # Core scanning logic
├── payloads.py # List of XSS, SQLi payloads
├── templates/
│ └── index.html # Frontend UI
├── static/
│ └── style.css # Optional CSS styling
└── reports/
└── scan_results.json # Output of latest scan

🧠 How It Works
a. **Crawling Input Fields**
- The scanner uses `requests` to fetch the target page and `BeautifulSoup` to parse HTML content.
- It identifies all `<form>` tags and extracts input fields for testing.

b. **Injecting Payloads**
- Predefined payloads from `payloads.py` (e.g., XSS and SQLi test strings) are injected into each form field.
- The form is submitted, and the server’s response is captured.

c. **Analyzing Responses**
- The scanner looks for payload reflection or signs of vulnerability in the response.
- For example, a reflected XSS payload (`<script>alert('XSS')</script>`) found in the response body is flagged.

d. **Flask Web Interface**
- A simple UI lets users enter a URL and start scans from the browser.
- Results are shown below the form, detailing vulnerabilities found.

e. **Logging & Reports**
- Detected issues are saved in `reports/scan_results.json`.
- Each entry includes:
  - Target URL
  - Payload used
  - Evidence from the response
  - Severity (e.g., Low, Medium, High)

✅ How to Use
1. **Clone the Repository**
```bash
git clone https://github.com/yourusername/vuln_scanner.git
cd vuln_scanner
2. Set Up Virtual Environment (Windows)
bash
python -m venv venv
venv\Scripts\activate
3. Install Required Libraries
bash
pip install flask requests beautifulsoup4
4. Run the Scanner
bash
python main.py
Then open your browser and go to:
cpp
http://127.0.0.1:5000
🧪 Testing
https://testphp.vulnweb.com — general test site with known vulnerabilities

📂 Example Output
Here’s what a result entry looks like in scan_results.json:
json
{ "url": "http://example.com/vulnerable-form",
  "vulnerability": "XSS",
  "payload": "<script>alert('XSS')</script>",
  "evidence": "<script>alert('XSS')</script>",
  "severity": "High"}

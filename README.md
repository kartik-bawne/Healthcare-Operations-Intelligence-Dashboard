
# 🏥 Healthcare Operations Intelligence Dashboard

> **A Python and Streamlit-based Business Intelligence & Decision Support System that transforms hospital operational data into actionable KPIs, interactive analytics, operational alerts, and management insights.**

The **Healthcare Operations Intelligence Dashboard** is an interactive Business Intelligence and Decision Support System developed to provide a centralized view of critical hospital operations.

The system processes operational data related to **patients, laboratory services, pharmacy, ambulance transportation, staff scheduling, appointments, operation theatres, and emergency monitoring**.

It transforms fragmented raw data into **cleaned datasets, decision-grade KPIs, interactive visualizations, operational alerts, trends, and decision-support insights** to help hospital administrators monitor performance and make faster, data-driven decisions.

### Core Workflow

**Raw Hospital Data → Data Cleaning → KPI Calculation → Interactive Dashboard → Alerts & Insights → Decision Support**

---

## 📊 Project Overview

Hospitals generate operational data across multiple departments and functions. When this information is maintained across separate spreadsheets, identifying operational bottlenecks, workload changes, resource utilization, and emerging trends can become difficult.

This project provides a centralized analytics layer that enables administrators to:

* Monitor important hospital operations from a single dashboard
* Track decision-relevant KPIs
* Identify operational bottlenecks
* Analyze patient and admission trends
* Monitor laboratory performance
* Analyze pharmacy demand and dispensing patterns
* Evaluate ambulance response and transportation metrics
* Monitor staff workload and scheduling
* Analyze appointment completion, cancellation, and no-show patterns
* Track operation theatre utilization
* Monitor emergency department trends
* Identify potential operational risks
* Generate plain-language alerts
* Generate summarized PDF reports

Rather than displaying excessive metrics, each dashboard module focuses on approximately **5–7 decision-relevant KPIs**, supported by interactive visualizations and actionable insights.

---

# 🏗️ Project Structure

```text
Healthcare-Operations-Intelligence-Dashboard/
│
├── Home.py                              # Application entry point + login
├── logo.png                             # Dashboard branding
├── README.md                            # Project documentation
├── requirements.txt                     # Python dependencies
├── LICENSE.md                            # MIT License
│
├── data/
│   └── Hospital_Dataset_Complete_Project.xlsx
│                                         # Bundled sample dataset
│
├── utils/
│   ├── __init__.py
│   ├── auth.py                           # Authentication & access control
│   ├── data_loader.py                    # Dataset loading & cleaning
│   ├── kpi.py                            # KPI calculations & alert rules
│   ├── pdf_generator.py                  # PDF report generation
│   └── styling.py                        # Dashboard design system
│
├── views/
│   ├── Overview.py                       # Executive overview
│   ├── Patient_Overview.py               # Patient analytics
│   ├── Laboratory.py                     # Laboratory analytics
│   ├── Pharmacy.py                       # Pharmacy analytics
│   ├── Ambulance.py                      # Ambulance analytics
│   ├── Staff_Scheduling.py               # Staff scheduling analytics
│   ├── Appointments.py                   # Appointment analytics
│   ├── OT_Dashboard.py                   # Operation theatre analytics
│   └── Emergency_Monitoring.py            # Emergency monitoring
│
└── .streamlit/
    ├── config.toml                       # Streamlit configuration
    ├── secrets.toml.example               # Example credentials format
    └── secrets.toml                      # Local credentials - NOT committed
```

---

# 📊 Dashboard Modules

## 1. Executive Overview

The **Overview** page provides an executive-level summary of hospital operations.

### Features

* Curated executive KPIs
* Operational alerts
* Patient trends
* Revenue trends
* Department performance
* Interactive charts
* Dataset upload functionality
* Decision-support insights
* PDF report generation

The page is designed to answer:

> **What is happening across hospital operations, what requires attention, and where should management focus?**

---

## 2. Patient Overview

**Source:** `Hospital_Visits`

### Key Analytics

* Patient demographics
* Hospital visits
* Admissions
* Billing information
* Patient satisfaction
* Operational trends

---

## 3. Laboratory

**Source:** `laboratory data`

### Key Analytics

* Laboratory test volume
* Revenue
* Test category distribution
* Technician workload
* Laboratory performance
* Testing trends

---

## 4. Pharmacy

**Source:** `pharmacy data`

### Key Analytics

* Pharmacy sales
* Medicine categories
* Branch performance
* Medicine demand
* Dispensing trends
* Demand intelligence

### Medicine Demand Intelligence

The source dataset does **not** contain a live `stock-on-hand` field.

Therefore, the dashboard does not present a fabricated stock count.

Instead, it uses **medicine dispensing velocity as a practical demand indicator/proxy** to identify fast-moving medicines and support demand monitoring and potential reorder decisions.

---

## 5. Ambulance

**Source:** `Ambulance_Transportation`

### Key Analytics

* Ambulance response time
* Travel time
* Fuel cost
* Driver workload
* Transportation trends

---

## 6. Staff Scheduling

**Source:** `Staff_Scheduling`

### Key Analytics

* Staff workload
* Leave rate
* Overtime
* Duty types
* Emergency coverage
* Scheduling trends

---

## 7. Appointments

**Source:** `Appointments`

### Key Analytics

* Completed appointments
* Cancelled appointments
* No-show rate
* Peak appointment hours
* Appointment trends

---

## 8. Operation Theatre Dashboard

**Source:** `OT_Dashboard`

### Key Analytics

* Surgery status
* Operation theatre utilization
* Room utilization
* Surgeon workload
* Surgery trends

---

## 9. Emergency Monitoring

**Source:** `ER_Monitoring_Summary`

### Key Analytics

* Emergency case trends
* Monthly emergency volume
* Emergency categories
* Seasonal patterns
* Heatmap-based analysis

---

# 🚨 Decision-Support Alerts

The dashboard goes beyond displaying raw numbers.

The KPI and intelligence layer converts important operational metrics into **plain-language alerts** that help administrators identify areas requiring attention.

### Example

```text
Bed occupancy is at 92% — prepare additional beds.

Appointment no-show rate is increasing —
review appointment confirmation procedures.

Emergency cases are increasing —
consider additional emergency coverage.

Medicine dispensing velocity is high —
monitor demand and reorder requirements.
```

The actual alerts are generated dynamically according to the underlying dataset and KPI rules.

### Decision-Support Flow

**Metric → Threshold/Trend Evaluation → Alert → Recommended Attention**

This transforms the dashboard from a simple visualization tool into an **operational decision-support layer**.

---

# 📈 KPI Intelligence Engine

The centralized KPI and alert logic is implemented through:

```text
utils/kpi.py
```

This module handles:

* KPI calculations
* Threshold evaluation
* Performance indicators
* Operational alerts
* Trend interpretation
* Decision-support rules

### KPI Design Philosophy

Each dashboard page intentionally focuses on approximately **5–7 decision-relevant KPIs**.

The design uses:

* One visually emphasized **hero KPI**
* Supporting operational KPIs
* Interactive charts
* Contextual alerts
* Plain-language insights

The objective is to reduce information overload and make important operational signals easier to identify.

---

# 🎨 Design System

The dashboard uses a centralized styling architecture through:

```text
utils/styling.py
```

This ensures a consistent visual language across all dashboard modules.

### Design Features

* Professional dashboard layout
* Gradient page headers
* KPI cards
* Alert cards
* Interactive chart containers
* Consistent typography
* Responsive layouts
* Custom stroke-based icons
* Highlighted important chart values
* Consistent filter bars
* Soft gradient application background
* Subtle UI animations

### Visualization Philosophy

Charts are designed to emphasize the **most decision-relevant information** rather than displaying a wall of identical visual elements.

Important values can be visually highlighted to help users quickly identify:

* Highest and lowest values
* Operational bottlenecks
* Increasing demand
* Resource pressure
* Important trends

---

# 🔐 Authentication & Access Control

The dashboard includes authentication to restrict access to hospital operational information.

### Authentication Flow

```text
Home.py
   ↓
Login Interface
   ↓
Session Authentication
   ↓
Access Validation
   ↓
Dashboard Navigation
```

Authentication is implemented through:

```text
Home.py
utils/auth.py
.streamlit/secrets.toml
```

`Home.py` handles the login interface, while `utils/auth.py` provides access protection for individual dashboard pages.

This prevents users from simply bypassing the login interface by directly opening an internal dashboard page.

---

## 🔑 Credential Management

Credentials are stored outside the application source code using:

```text
.streamlit/secrets.toml
```

The repository should contain only:

```text
.streamlit/secrets.toml.example
```

Real credentials must never be committed to GitHub.

### Demo Credentials

For local/project demonstration:

```text
Username: admin
Password: admin123
```

> ⚠️ These credentials are for demonstration purposes only. Change them before any real deployment.

---

# 📄 PDF Report Generation

The project includes a dedicated PDF reporting module:

```text
utils/pdf_generator.py
```

The dashboard can generate summarized PDF reports containing important operational information and insights.

Potential uses include:

* Management reporting
* Operational review meetings
* Decision-support summaries
* Offline analysis
* Documentation of dashboard findings

---

# 📂 Dataset

The project uses a bundled sample hospital dataset:

```text
data/Hospital_Dataset_Complete_Project.xlsx
```

The application expects the following worksheet names:

```text
Hospital_Visits
laboratory data
pharmacy data
Ambulance_Transportation
Staff_Scheduling
Appointments
OT_Dashboard
ER_Monitoring_Summary
```

The application supports two approaches:

### Bundled Dataset

The included Excel workbook can be loaded automatically from the `data/` directory.

### Custom Dataset

Users can upload another workbook through the dashboard.

No application code changes are required as long as the replacement workbook follows the expected worksheet and column structure.

---

# 🛠️ Technology Stack

| Technology       | Purpose                                   |
| ---------------- | ----------------------------------------- |
| **Python**       | Core programming language                 |
| **Streamlit**    | Interactive dashboard and web application |
| **Pandas**       | Data loading, cleaning and analysis       |
| **Plotly**       | Interactive data visualization            |
| **OpenPyXL**     | Excel file processing                     |
| **ReportLab**    | PDF report generation                     |
| **Git & GitHub** | Version control and project hosting       |

---

# ⚙️ Installation

## Requirements

* Python **3.10+**
* pip
* Git

---

## 1. Clone the Repository

```bash
git clone https://github.com/kartik-bawne/Healthcare-Operations-Intelligence-Dashboard.git
```

Move into the project directory:

```bash
cd Healthcare-Operations-Intelligence-Dashboard
```

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
```

Activate:

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
```

Activate:

```bash
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

# 🔑 Configure Credentials

Create the local secrets file from the example:

### Windows

```bash
copy .streamlit\secrets.toml.example .streamlit\secrets.toml
```

### Linux / macOS

```bash
cp .streamlit/secrets.toml.example .streamlit/secrets.toml
```

Then edit:

```text
.streamlit/secrets.toml
```

with your own credentials.

> **Important:** Never commit `.streamlit/secrets.toml` to GitHub.

---

# ▶️ Run the Application

Start the application:

```bash
streamlit run Home.py
```

The application will normally be available at:

```text
http://localhost:8501
```

### Demo Login

```text
Username: admin
Password: admin123
```

---

# ☁️ Deployment

The application can be deployed on **Streamlit Community Cloud** or another platform capable of running Streamlit applications.

## Streamlit Community Cloud

1. Push the repository to GitHub.
2. Open Streamlit Community Cloud.
3. Select **New App**.
4. Select this repository.
5. Select the required branch.
6. Set the main file to:

```text
Home.py
```

7. Configure the required credentials under **Settings → Secrets**.
8. Deploy the application.

Dependencies are installed using:

```text
requirements.txt
```

> Do not upload or commit your local `.streamlit/secrets.toml`.

---

# 🐳 Docker Deployment

A basic Docker deployment can use:

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY . .

RUN pip install --no-cache-dir -r requirements.txt

EXPOSE 8501

CMD ["streamlit", "run", "Home.py", "--server.address=0.0.0.0"]
```

---

# 🔒 Security Practices

The project follows basic credential-protection practices for a development and demonstration environment.

The following should never be committed:

```text
venv/
.venv/
__pycache__/
*.pyc
.env
.streamlit/secrets.toml
```

Only the example configuration should be committed:

```text
.streamlit/secrets.toml.example
```

Never commit:

* Passwords
* API keys
* Authentication tokens
* Database credentials
* Private keys
* Other sensitive information

If real credentials are accidentally pushed to GitHub, they should be considered compromised and **rotated immediately**.

### Production Security Note

This project should be considered a **development/academic decision-support application**, not a production hospital information system.

A real healthcare deployment would require additional controls such as:

* Strong identity and access management
* Role-based permissions
* Encryption
* Secure session management
* Audit logging
* Infrastructure security
* Data privacy controls
* Applicable healthcare and privacy compliance requirements

---

# 🧪 Troubleshooting

| Problem                     | Solution                                             |
| --------------------------- | ---------------------------------------------------- |
| `ModuleNotFoundError`       | Run `pip install -r requirements.txt`                |
| Login fails                 | Check `.streamlit/secrets.toml`                      |
| Dataset not loading         | Verify the Excel file and worksheet names            |
| Blank/old data after upload | Refresh the browser                                  |
| Port already in use         | Run `streamlit run Home.py --server.port 8502`       |
| No dataset loaded yet       | Open the Overview page first                         |
| PDF generation error        | Verify PDF dependencies are installed                |
| Streamlit deployment fails  | Check `requirements.txt` and Streamlit Cloud Secrets |

---

# 🚀 Future Scope

The current system provides an interactive analytics and decision-support foundation.

Future improvements can include:

### Data & Infrastructure

* Real-time hospital database integration
* Cloud database connectivity
* Automated ETL pipelines
* API-based data ingestion
* Real-time hospital IoT integration

### Predictive Analytics

* Patient admission forecasting
* Emergency demand prediction
* Medicine demand forecasting
* Staff requirement prediction
* Advanced anomaly detection
* Predictive operational analytics
* Machine-learning-based decision support

### Security & Access

* Role-based access control
* Department-level permissions
* Advanced audit logging
* Enterprise authentication

### Automation

* Automated email reports
* Scheduled management reports
* Automated operational alerts
* Predictive alerting

---

# 🎯 Project Objective

The primary objective of the **Healthcare Operations Intelligence Dashboard** is to transform fragmented hospital operational data into a centralized decision-support system.

Instead of manually analyzing multiple spreadsheets, hospital administrators can monitor critical operational metrics through a single interactive interface and quickly identify:

* Operational bottlenecks
* Increasing workload
* Emergency trends
* Appointment issues
* Resource utilization
* Staff workload
* Pharmacy demand
* Laboratory performance
* Patient-related trends
* Revenue and operational patterns

This enables **faster, clearer, and more data-driven operational decision-making**.

---

# 💡 From Data to Decisions

The central concept of the project is:

```text
RAW HOSPITAL DATA
        ↓
DATA CLEANING
        ↓
KPI ENGINE
        ↓
ANALYTICS
        ↓
INTERACTIVE VISUALIZATION
        ↓
ALERT GENERATION
        ↓
DECISION SUPPORT
        ↓
PDF REPORTING
```

The objective is not simply to create charts.

The system is designed to bridge the gap between:

**Data → Insight → Action**

A hospital administrator should be able to understand:

> **What is happening?**

> **Where is attention required?**

> **What operational trend is emerging?**

> **What should management investigate or act upon?**

---
## 📑 Project Presentation

The complete project presentation is available here:

[📥 View / Download Project Presentation](docs/Development%20of%20a%20Healthcare%20Operations%20Intelligence%20Dashboard%20with%20Decision%20Analytics%20Group%201.pdf)

## 📄 Project Report

The complete project report is available here:

[📥 View / Download Project Report](docs/Healthcare_Intelligence_Report.pdf)


# 📌 One-Line Summary

> **A Python and Streamlit Business Intelligence system that transforms hospital operational data into a secure, interactive decision-support dashboard with curated KPIs, intelligent alerts, interactive visualizations, and PDF reporting for faster data-driven healthcare operations.**

---

# 📜 License

This project is licensed under the **MIT License**.

See [`LICENSE.md`](LICENSE.md) for details.

---

# 👨‍💻 Author

**Kartik Bawne**

Healthcare Operations Intelligence Dashboard

Built with:

**Python • Streamlit • Pandas • Plotly • OpenPyXL • ReportLab**

---

## ⭐ Project Focus

**Healthcare Operations • Business Intelligence • Decision Analytics • Data Visualization • Python • Streamlit • Operational Intelligence**

[1]: https://github.com/kartik-bawne/Healthcare-Operations-Intelligence-Dashboard "GitHub - kartik-bawne/Healthcare-Operations-Intelligence-Dashboard: Healthcare Operations Intelligence Dashboard developed during Infosys Springboard Virtual Internship. · GitHub"

🛡️ SentinelCloud: AI-Powered Uptime Monitor

This is a full-stack monitoring solution designed to track website availability and detect performance anomalies in real-time. Using a "Rolling Window" statistical approach, the system identifies when a website's response time is significantly higher than its historical average, providing actionable "Warning" alerts rather than just simple "Down" notifications.
____________________________________

🚀 Key Features

Automated Monitoring: A background "Sentinel" worker that pings target URLs at regular intervals. (Sentinel simply means a security guard)

Machine Learning Brain: An analytics engine built with Pandas and Scikit-learn that calculates rolling averages and standard deviations to detect latency anomalies.

Containerized Database: Uses Docker to host a PostgreSQL database, ensuring data persistence and easy environment setup.

Interactive API: A FastAPI backend with automated Swagger UI documentation for testing monitoring endpoints.
____________________________________

🛠️ Tech Stack
Language: Python 3.x.

Backend Framework: FastAPI.

Database: PostgreSQL via Docker.

Data Science: Pandas, Scikit-learn (for anomaly detection).

Environment: Virtualenv (venv).

____________________________________

📦 Installation & Setup

1. Clone the Repository

Bash
git clone https://github.com/[YOUR-USERNAME]/sentinel-cloud.git
cd sentinel-cloud

2. Set Up Infrastructure

Ensure Docker Desktop is running, then start the database container:

Bash
docker ps # Verify sentinel-db is running

3. Install Dependencies

Bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

🚦 How to Run
Tab 1: Start the API (The Gatekeeper)

Bash
uvicorn main:app --reload
Visit http://127.0.0.1:8000/docs to view the interactive API documentation.

Tab 2: Start the Sentinel (The Worker)

Bash
python monitor.py

Tab 3: Get AI Analytics

You can fetch a health report for any monitor by calling the analytics endpoint: GET /monitors/{id}/analytics
____________________________________

🧠 The Anomaly Detection Logic

SentinelCloud doesn't just check if a site is "Up." It uses the following logic to assess health:

Fetches the last 10 pings for a specific monitor.

Calculates the Mean and Standard Deviation.

Flags an Anomaly if the latest ping exceeds Average + (2 * StdDev).
____________________________________

📬 Future Roadmap
Frontend Dashboard: A "nice and simple" user interface built with Tailwind CSS and JavaScript.

Real-time Alerts: Integration with Slack or Email notifications when an anomaly is detected.
____________________________________


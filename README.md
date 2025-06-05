# 🚀 Data Ingestion API System

A RESTful API system built with Node.js and Express that ingests ID lists, processes them in batches asynchronously, prioritizes based on urgency, and provides status updates. It enforces strict rate limiting and handles background job processing.

---

## 🌐 Live Demo

🔗 Hosted URL: data-ingestion-api-production-d542.up.railway.app 
you can use postman or thunderclient to test the API endpoints

---

## 📦 API Endpoints

### 1. `POST /ingest`

Ingest a list of IDs with a priority.
![alt text](<screenshots/Screenshot 2025-06-05 110711.png>)
![alt text](<screenshots/Screenshot 2025-06-05 111615.png>)

**Request Body:**

```json
{
  "ids": [1, 2, 3, 4, 5],
  "priority": "HIGH"
}
```
![alt text](<screenshots/Screenshot 2025-06-05 110731.png>)
![alt text](<screenshots/Screenshot 2025-06-05 111749.png>)


**Response:**

```json
{
  "ingestion_id": "abc123"
}
```

- Accepts priorities: `HIGH`, `MEDIUM`, `LOW`
- Only 3 IDs are processed at a time.
- Rate limited: **1 batch every 5 seconds**
- Higher priority jobs are processed first (FIFO within same priority)

---
![alt text](<screenshots/Screenshot 2025-06-05 110806.png>)

### 2. `GET /status/:ingestion_id`

Get the status of an ingestion request.

![alt text](<screenshots/Screenshot 2025-06-05 110815.png>)

## ⚙️ How It Works

- Incoming ingestion requests are split into batches (3 IDs per batch).
- Batches are processed asynchronously with a **5-second interval** between each.
- A background job runner handles all execution.
- In-memory queueing and priority scheduling ensures proper job ordering.

---

## 🧪 Running Locally

### 1. Clone the Repo

```bash
git clone https://github.com/Anmol-Sharma126/data-ingestion-api.git
cd data-ingestion-api
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Run the Server

```bash
npm start
```

> Server runs at `http://localhost:5000`

---

## 🧪 Testing

```bash
npm test
```

Tests include:
- Rate limit enforcement
- Priority ordering
- Status accuracy

---

## 📤 Deployment

This project is deployed on **Railway**. You can redeploy by:

1. Forking the repo
2. Connecting it to Railway
3. Setting `npm start` as your start command

---

## 👨‍💻 Author

**Anmol Sharma**  
GitHub: [@Anmol-Sharma126](https://github.com/Anmol-Sharma126)

---

## ✅ Status

🟢 LIVE and TESTED
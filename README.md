# FastAPI YOLOv8 Image Analysis API

This repository contains a production-ready Image Analysis API built using FastAPI, YOLOv8, JWT Authentication, Rate Limiting, and Request Logging.  
The API accepts an image file, performs object detection using YOLOv8, and returns all detections with labels, confidence scores, and bounding box coordinates.

---

## Features
- FastAPI-based high-performance backend  
- YOLOv8 object detection (Ultralytics)  
- JWT authentication with protected routes  
- Rate limiting (5 requests/minute per user)  
- Centralized logging of all API usage  
- File upload via multipart/form-data  
- Clean and structured JSON responses  
- Easy to deploy and extend  

---

## Project Structure
```
fastapi-yolov8-api/
│── main.py
│── yolov8n.pt
│── app.log
│── requirements.txt
│── README.md
```

---

## Technology Stack

| Component        | Technology     |
|------------------|----------------|
| Framework        | FastAPI        |
| Model            | YOLOv8n        |
| Authentication   | JWT (PyJWT)    |
| Rate Limiting    | SlowAPI        |
| Logging          | Python logging |
| Server           | Uvicorn        |

---

## Installation

### 1. Clone the repository
```
git clone https://github.com/HarshPrasad123/fastapi-yolov8-api
cd fastapi-yolov8-api
```

### 2. Install dependencies
```
pip install -r requirements.txt
```

### 3. Start the server
```
uvicorn main:app --reload
```

Server available at:

```
http://127.0.0.1:8000
```

---

## Authentication

### Endpoint  
`POST /login`

### Body (form-data)
| Key       | Value     |
|-----------|-----------|
| username  | harsh     |

### Example Response
```json
{
  "token": "your.jwt.token"
}
```

Use this token for all protected endpoints.

---

## Image Analysis Endpoint

### Endpoint  
`POST /analyze`

### Headers
```
Authorization: Bearer <your_token>
```

### Body (form-data)
| Key    | Type | Value          |
|--------|------|-----------------|
| image  | file | any image file |

### Example Response
```json
{
  "detections": [
    {
      "class": 0,
      "label": "person",
      "confidence": 0.94,
      "bbox": [34, 61, 189, 300]
    }
  ]
}
```

---

## Rate Limiting

Each user is limited to 5 requests per minute.  
If exceeded, the server returns:

```json
{"detail": "Rate limit exceeded"}
```

---

## Logging

All requests are logged in `app.log` with timestamps and user identifiers.

Example log entry:
```
User harsh analyzed an image.
```

---

## Contributing

Contributions, issues, and feature requests are welcome.  
You may fork this repository and submit a pull request.

---

## License

This project is intended for educational and research purposes.

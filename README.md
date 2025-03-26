# AWS-Based QR Code Generator

## Section 1: Project Description

A serverless QR Code Generator using AWS Lambda and Amazon S3. Users can input text or a URL via a web interface, which triggers an AWS Lambda function to generate a QR code. The generated code is saved in an S3 bucket and provided to the user via a downloadable link.

---

## Section 2: Overview

### 2.1 Purpose
This project aims to deliver a fast, scalable, and cost-effective way to generate QR codes in the cloud without maintaining any backend server.

### 2.2 Scope
- Users input text/URLs in a web form.
- Lambda function generates a QR code.
- QR code stored in S3 bucket.
- Users receive a pre-signed download URL.

### 2.3 Requirements

#### 2.3.1 Functional Requirements
- Accept user input from a web form.
- Generate QR code via Lambda.
- Save QR code in S3.
- Return a downloadable link to the user.

#### 2.3.2 Non-Functional Requirements
- Response time < 2 seconds.
- 99.9% uptime.
- Support multiple concurrent requests.

#### 2.3.3 Technical Requirements
- AWS Lambda, S3, API Gateway
- Python (backend)
- HTML, CSS, JS (frontend)
- Git, AWS CLI

#### 2.3.4 Security Requirements
- API Gateway with API key access
- IAM roles for Lambda and S3
- HTTPS enforced

#### 2.3.5 Estimates

| Task | Description                            | Est. Hours |
|------|----------------------------------------|------------|
| 1    | Set up AWS Lambda and permissions      | 4 hrs      |
| 2    | Create S3 bucket & integration         | 2 hrs      |
| 3    | Write QR code generation logic         | 3 hrs      |
| 4    | Design and build frontend              | 2 hrs      |
| 5    | Connect frontend to API Gateway        | 2 hrs      |
|      | **Total**                              | **13 hrs** |

#### 2.3.6 Traceability Matrix

| Requirement | Module                          |
|-------------|----------------------------------|
| R1          | User input (web form)            |
| R2          | QR code generation (Lambda)      |
| R3          | Storage (S3 bucket)              |
| R4          | File access (pre-signed URL)     |

---

## Section 3: System Architecture

### 3.1 Overview
Frontend communicates with API Gateway → triggers Lambda → generates and stores QR code in S3 → returns download link.

### 3.2 Architectural Diagram
![image](https://github.com/user-attachments/assets/4cf7c65b-5b62-4517-8073-588e8cd3f246)

---

## Section 4: Data Dictionary

| Field       | Type     | Description                    |
|-------------|----------|--------------------------------|
| ID          | String   | Unique request identifier      |
| Input       | String   | User-provided text/URL         |
| FileName    | String   | Generated image file name      |
| S3_URL      | String   | Pre-signed link to QR code     |
| Timestamp   | DateTime | Time of request                 |

---

## Section 5: Data Design

### 5.1 Persistent Data Model

**Entity: QRCode**
- ID (PK)
- InputText
- QRImageName
- QRImageURL
- Timestamp


---

## Section 6: User Interface Design

### 6.1 UI Overview
Simple form with:
- Input text box
- "Generate QR Code" button
- Image + download link on success

### 6.2 Navigation Flow
Home → Form → Submit → Display QR Code

### 6.3 Use Cases
**Generate QR Code:**
- User enters text or URL
- Clicks button
- Receives QR image and link

---


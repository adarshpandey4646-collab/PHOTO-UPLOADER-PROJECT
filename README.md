Overview
This project is a small end-to-end prototype that allows a user to upload a child’s photo and generates a personalised illustration by inserting a stylised version of the child’s face into a provided illustration.
The goal of this assignment is to demonstrate:
Practical AI model selection
Clean end-to-end system design
Image processing and orchestration
Reasoned trade-offs and limitations
Features
Simple image upload UI
Automatic face detection
Identity-preserving face stylisation
Illustration-style image generation
Backend AI orchestration
Deployed, usable prototype
Tech Stack
Frontend
Next.js (React)
Image upload + preview UI
Hosted on Vercel

Backend

Python + FastAPI

GPU-based inference

Hosted on Replicate / AWS / similar

AI Models

Instant-ID (identity preservation)

Stable Diffusion XL (SDXL) for illustration-style generation

InsightFace for face detection and embeddings



ARCHITECTURE DIAGRAM 

+----------------------+
|      User Browser    |
|  (Child Photo Upload)|
+----------+-----------+
           |
           | Upload Image
           v
+----------------------+
|   Frontend (Next.js) |
|  - Image Upload UI   |
|  - Preview Result    |
+----------+-----------+
           |
           | POST /generate
           | multipart/form-data
           v
+----------------------+
| Backend (FastAPI)    |
|  - Request Handling  |
|  - Validation        |
+----------+-----------+
           |
           | Face Crop & Embedding
           v
+----------------------+
| Face Detection Layer |
| (InsightFace)        |
+----------+-----------+
           |
           | Identity Embeddings
           v
+------------------------------+
| AI Generation Pipeline       |
| - Instant-ID                 |
| - Stable Diffusion XL        |
| - Illustration Prompt        |
+----------+-------------------+
           |
           | Stylised Image
           v
+----------------------+
| Image Composition    |
| - Face Blending      |
| - Final Illustration |
+----------+-----------+
           |
           | Image URL
           v
+----------------------+
|   Frontend Display   |
| (Personalised Image) |
+----------------

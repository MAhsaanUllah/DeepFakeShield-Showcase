# DeepFakeShield

<img src="https://img.shields.io/badge/Python-3.11-blue.svg" alt="Python">
<img src="https://img.shields.io/badge/FastAPI-0.104-009688.svg" alt="FastAPI">
<img src="https://img.shields.io/badge/PyTorch-2.x-EE4C2C.svg" alt="PyTorch">
<img src="https://img.shields.io/badge/React-19-61DAFB.svg" alt="React">
<img src="https://img.shields.io/badge/Vite-7.x-646CFF.svg" alt="Vite">
<img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License">
<img src="https://img.shields.io/badge/Project-FYP%202026-orange.svg" alt="Status">

DeepFakeShield is an AI-powered image forensics platform that detects manipulated and AI-generated face images using deep learning.
It combines a React frontend, FastAPI backend, and a PyTorch inference pipeline for real-time classification.

## Project Highlights

- Multi-class face image detection (Real, Fake, AI-Generated)
- End-to-end web workflow: upload image, run inference, return confidence score
- FastAPI API service connected to trained model checkpoints
- React + Vite responsive frontend for fast interaction
- Modular architecture for easy model replacement and experimentation

## What Is Already Implemented

- Image upload pipeline from frontend to backend
- Model loading and inference in backend services
- Prediction response with class label and confidence
- Dataset preprocessing/training structure for multiple model variants
- Checkpoint-based model serving setup
- Local development workflow for both frontend and backend

## Future Implementation (Next Phase)

- Video deepfake detection with frame-level aggregation
- Explainable AI outputs (Grad-CAM / attention heatmaps)
- Ensemble inference across multiple backbones
- Authentication + user session history
- Cloud deployment with CI/CD and model versioning
- Monitoring dashboards (latency, confidence drift, throughput)
- Adversarial robustness and out-of-distribution checks
- API rate limiting and production hardening

## UI + Full Technical Diagram

```mermaid
flowchart LR
		U[User] --> FE[React + Vite Frontend]
		FE --> C1[UploadForm]
		FE --> C2[ModelSelector]
		FE --> C3[ResultCard]
		C1 --> API[API Service Layer]

		API --> R1[FastAPI Route: /predict/image]
		R1 --> S1[Image Service]
		S1 --> P1[Preprocessing Pipeline]
		P1 --> M1[PyTorch Model Inference]
		M1 --> O1[Softmax + Confidence Scoring]
		O1 --> R2[JSON Response]
		R2 --> C3

		D1[(Processed Dataset)] --> T1[Training Scripts]
		T1 --> CK[(Model Checkpoints)]
		CK --> M1

		subgraph Frontend
			FE
			C1
			C2
			C3
			API
		end

		subgraph Backend
			R1
			S1
			P1
			M1
			O1
			R2
		end

		subgraph ML Pipeline
			D1
			T1
			CK
		end
```

## Tech Stack

- Python, FastAPI, Uvicorn
- PyTorch, TorchVision, OpenCV, Pillow
- React, Vite, JavaScript
- Docker (deployment-ready structure)

## Use Cases

- Academic research on synthetic media detection
- Awareness and educational demonstration
- Assistive screening for suspicious facial imagery
- Prototype foundation for media integrity systems

## Project Status

Active Final Year Project (2026), currently focused on improving robustness, explainability, and deployment readiness.

## Responsible Use

DeepFakeShield is an assistive detection tool and should be used with human verification in high-stakes scenarios.
Model outputs are probabilistic and may vary across unseen generators or highly compressed media.

## License

MIT License (or replace with your preferred license).
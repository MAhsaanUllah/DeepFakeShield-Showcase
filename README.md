🛡️ DeepFakeShield
Enterprise-Grade Deepfake & Synthetic Media Detection System
PythonPyTorchFastAPIReactDockerAzure


DeepFakeShield is a production-ready AI forensics platform engineered to combat the rise of manipulated media. Going beyond standard binary classifiers, it utilizes a custom-trained Soft-Voting CNN Ensemble and an innovative Gemma-3 Vision-Language Model (VLM) fallback layer to distinguish between Real, Fake (Deepfakes), and AI-Generated (Fully Synthetic) states, providing human-readable forensic proof for every scan.

⚠️ RECRUITER NOTE: This repository serves as a Technical Showcase. The underlying source code, proprietary models, and Azure deployment configurations are maintained privately as part of a final year commercial-grade project.

🏗️ Repository Architecture & Code Structure
The project strictly follows a decoupled microservices-style layout, separating the inference engine from the client layer.

text

📦 DeepFakeShield-FYP
 ┣ 📂 backend
 ┃ ┣ 📂 app
 ┃ ┃ ┣ 📂 api               # FastAPI Endpoints (Video/Image/Telemetry)
 ┃ ┃ ┣ 📂 services          # Media extraction & PyTorch Inference logic
 ┃ ┃ ┣ 📜 main.py           # Uvicorn entry point, CORS, Rate Limiter
 ┃ ┃ ┗ 📜 db.py             # Asynchronous SQLite Telemetry mappings
 ┃ ┣ 📜 requirements.txt
 ┃ ┗ 📜 Dockerfile          # Multi-stage CPU-optimized build
 ┣ 📂 frontend
 ┃ ┣ 📂 src
 ┃ ┃ ┣ 📂 components        # React UI (UploadForm, ResultCard, ModelSelector)
 ┃ ┃ ┣ 📂 services          # API integration with AbortController timeouts
 ┃ ┃ ┣ 📂 styles            # High-contrast Slate-Zinc design tokens
 ┃ ┃ ┗ 📜 App.jsx           # Main Shell & Analytics Dashboard
 ┃ ┣ 📜 package.json
 ┃ ┗ 📜 vercel.json         # Routing constraints
 ┗ 📂 ai_models
   ┣ 📂 checkpoints         # Encrypted weights (.pth) for Ensemble CNNs
   ┗ 📜 train.py            # AdamW, Cosine Scheduler & AMP training scripts
🕸️ System Flow & Logic Graph
HTTPS POST Payload
Allow
Yes: Real
No / Fake / AI
React/Vite Frontend
FastAPI Azure Backend
Rate Limit Check
Media Processing / OpenCV Haar
PyTorch CNN Ensemble
XceptionNet-41
EfficientNet-B4
MobileNetV3
Confidence > 85%?
Return Classification & Bounding Box
HuggingFace Gemma-3 VLM
Generate XAI Forensic Justification
SQLite Telemetry Logger
🌟 The Impact & Why It Matters
In an era of generative AI, detecting deepfakes is no longer enough; understanding why media is flagged is critical for journalism, judicial systems, and cybersecurity. DeepFakeShield solves this by combining high-speed spatial detection with Generative AI reasoning to deliver a transparent, scalable, and secure SaaS solution.

🚀 Enterprise Architectural Features
1. Hybrid Multi-Model Detection Engine (AI Core)
Ensemble Consensus Algorithm: Averaged standardized probability distributions from three parallel CNN backbones to yield a highly balanced, robust final prediction, eliminating single-model bias.
Dynamic Face Annotation: Server-side OpenCV Haar Cascades automatically isolate the region of interest (ROI) and render color-coded bounding boxes natively onto base64-encoded image payloads.
Video Inference Pipeline: Extracts and buffers 1 frame per second temporally, leveraging majority-voting algorithms to yield highly accurate video-level forensics without GPU memory exhaustion.
2. Gemma-3 VLM (Explainable AI Layer)
Standard probability percentages are insufficient for high-security environments. DeepFakeShield bridges this gap with XAI (Explainable AI):

Uncertainty Fallbacks: If the ensemble confidence drops below 85%, media is dynamically routed to Google's Gemma-3-4B-IT multimodal model via the Hugging Face API.
Forensic Justification: Gemma acts as a digital forensics expert, writing plain-English anomaly descriptions (e.g., analyzing uneven iris reflections, blending borders, or diffusion artifacts) to justify classifications.
3. Decoupled SaaS Infrastructure & Analytics
React/Vite Frontend: Features a Slate-Zinc high-contrast design system, a 3-tab upload interface (File, Video URL, Camera), and a lightning-fast UX.
Telemetry Dashboard: A real-time analytics panel mapping live scanning traffic, model usage percentages, and classification distributions (Real vs Fake) via asynchronous SQLite database logging. Secure CSV log exporting is available for offline auditing.
FastAPI Docker Backend: Deployed on an Azure Virtual Machine via multi-stage Dockerfiles utilizing CPU-optimized PyTorch execution environments.
4. DevSecOps & Security Hardening
CORS Lockdown: Strict origin whitelisting mapping exclusively to production Vercel environments.
In-Memory Rate Limiting: Token-bucket style sliding window middleware restricts API access to 5 scans per minute per client IP, preventing DDoS and server abuse.
Payload Constraints: Strict multipart file-size validations (Max 5MB for images, 50MB for video streaming) enforced at the route level to prevent buffer overflow attacks.
🧠 Machine Learning Metrics & Benchmarks
Backbone Architecture	Parameters	Input Resolution	Target Class	Strategic Role
XceptionNet-41	24.9M	299x299	3-Class	Primary (Micro-texture & boundary detection)
EfficientNet-B4	17.5M	380x380	3-Class	Secondary (Fine-grained structural features)
MobileNetV3-Large	4.2M	224x224	3-Class	High-Speed Tie-Breaker (Low latency)
🏆 Validation Performance: The ensemble model achieved an optimized 95.83% Accuracy with an F1-Score of 0.96 across diverse datasets including FaceForensics++, Celeb-DF, and StyleGAN. Inference latency remains under <1s for images.

🔮 Future Roadmap (Phase 2)
Unified Memory Caching: Consolidating @lru_cache model loaders across media services to halve backend RAM consumption.
Proactive Watermarking (SynthID): Combining reactive neural forensic detection with proactive cryptographic watermarking verification.
Multi-Modal Deepfakes: Extending the PyTorch processing pipeline to analyze audio waveforms for voice cloning detection.
ONNX Quantization: Exporting models to ONNX (INT8) to compress tensor weights for edge-device WASM execution.
Designed, Architected, and Developed by Muhammad Ahsaan Ullah (2026)
Open to Full-Stack & AI Engineering Opportunities

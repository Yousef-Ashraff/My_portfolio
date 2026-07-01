# Projects Added This Session (for CV)

---

## BNU Admission Chatbot – Multilingual RAG Assistant

Built a bilingual RAG chatbot that answers prospective students' admission questions in Arabic
(Egyptian & MSA), Franco-Arabic, and English, backed by a hybrid retrieval pipeline combining
dense search (Pinecone, bge-m3 embeddings) with sparse BM25, fused via reciprocal rank fusion and
rescored with an optional Cohere reranker. An intent router short-circuits greetings, FAQs, and
out-of-scope messages without an LLM call, while a Google Drive auto-sync job keeps the knowledge
base current by detecting new, modified, and deleted source PDFs every 10 minutes. Shipped as a
FastAPI service with a RTL/LTR-aware vanilla JS frontend, response caching, and Docker deployment.

**Highlights**
- 4 languages/dialects supported (Arabic MSA, Egyptian dialect, Franco-Arabic, English)
- Hybrid dense + sparse (BM25) retrieval with RRF fusion
- Automated Google Drive knowledge-base sync every 10 minutes
- Intent routing avoids unnecessary LLM calls for greetings/FAQs/out-of-scope

**Tech Stack:** FastAPI, Groq, Pinecone, BM25, Cohere, HuggingFace, Google Drive API, Docker

---

## Video Action Recognition on UCF50

Trained a deep learning model to classify human actions in video across 50 action categories from
the UCF50 dataset — from sports (basketball, diving, javelin throw) to everyday activities
(drumming, juggling, push-ups). Built a video preprocessing pipeline that samples a fixed number of
frames per clip, resizes and normalizes them, and feeds the resulting sequence into a
Keras/TensorFlow spatio-temporal classifier. Wrapped the trained model in an interactive Gradio web
app that accepts uploaded video files, transcodes them with FFmpeg, and returns the top-3 predicted
actions with confidence scores.

**Highlights**
- 50 action classes classified from raw video input
- 20 frames sampled, resized, and normalized per clip
- Interactive Gradio demo with top-3 confidence-scored predictions

**Tech Stack:** TensorFlow, Keras, OpenCV, Gradio, FFmpeg, NumPy

---

## Face Recognition – Identity-Verified Account Access

Built a facial-recognition identity verification system using a pretrained FaceNet (Inception)
encoder to generate 128-d face embeddings, with MTCNN handling automatic face detection and
cropping before encoding. New users enroll by uploading a few face images to build their embedding
profile; returning users are recognized by computing the L2 distance between their live capture and
every stored embedding, matching against the closest identity below a distance threshold. Wrapped
the pipeline in an interactive Gradio app that simulates a secure bank-account flow — scan face to
log in, then create an account or deposit/withdraw funds — and deployed it live on HuggingFace
Spaces.

**Highlights**
- 128-d FaceNet embeddings for face representation
- L2 distance-based identity matching against a stored embedding database
- 30+ identities in the demo dataset
- Live deployment on HuggingFace Spaces

**Tech Stack:** TensorFlow, FaceNet, MTCNN, Gradio, NumPy

---

## Twitter Sentiment Analysis with Apache Spark & Docker

Built a distributed sentiment analysis pipeline on a 3-node Apache Spark cluster (1 master + 2
workers), fully containerized with Docker Compose, to classify tweets into Positive, Negative,
Neutral, or Irrelevant. The Spark MLlib pipeline cleans and tokenizes raw text, strips stopwords,
extracts 20,000 TF-IDF features via HashingTF + IDF, and trains a Logistic Regression classifier on
~75K labeled tweets — reaching 91.7% training / 80.2% validation accuracy. The trained pipeline
model is served through a Flask web app for real-time predictions, returning the predicted class
alongside a full confidence breakdown across all four categories, plus a REST endpoint for
programmatic access.

**Highlights**
- 80.2% validation accuracy / 91.7% training accuracy on ~75K tweets
- 20,000 TF-IDF features via distributed Spark MLlib pipeline
- 3-node Dockerized Spark cluster (1 master, 2 workers)
- Flask REST API + web UI for real-time predictions

**Tech Stack:** Apache Spark, PySpark MLlib, Flask, Docker Compose, Logistic Regression, TF-IDF

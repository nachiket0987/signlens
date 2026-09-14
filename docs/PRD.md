# Product Requirement Document (PRD) — SignLens

**Project Name:** SignLens  
**Project Description:** End-to-End Deep Learning Pipeline for Real-Time Sign Language Recognition using YOLOv5 and Flask.  
**Author:** Nachiket Gadilohar  
**Version:** 1.0.0  

---

## 1. Executive Summary & Problem Statement
Over 70 million deaf and hard-of-hearing individuals worldwide face communication barriers daily. Existing sign language translation tools suffer from high latency, low detection accuracy, and lack of real-time camera inference support.

SignLens is a computer vision and deep learning platform powered by YOLOv5. It captures video frames via WebRTC/Flask, detects hand gestures and sign language tokens in real time, and translates them into natural language text and speech output.

---

## 2. Core Features
1. **Real-Time YOLOv5 Gesture Detector**: Detects sign language hand gestures at 30+ FPS.
2. **Flask & WebRTC Streaming Backend**: Streams video frames from web/mobile cameras.
3. **Speech Synthesis Engine**: Converts predicted sign text into audible speech using Text-to-Speech (TTS).

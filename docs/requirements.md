# WhatsApp Health Assessment Assistant

An on-device multimodal AI assistant that combines computer vision and a Llama
language model to give safe, general health guidance. It runs on an Arm-based
Android smartphone, and replies are shared through WhatsApp.

## Problem Statement
Meta Edge AI Challenge, Problem Statement 1: WhatsApp Health Assessment
Assistant (Healthcare theme).

## Modules
- **M1 Nutrition:** meal photo + question, giving general nutrition guidance
- **M2 General health Q&A:** text questions about general health awareness
- **M3 Medication label reader (optional):** reads a medicine box and gives general information only
- **M4 Health diary (optional):** summarises daily health notes

## Approach
- **Vision:** a small image classification model, exported with ExecuTorch
- **Reasoning:** a quantised Llama model running on-device via ExecuTorch
- **App:** an Android (Kotlin) app with image and text input
- **Safety:** confidence thresholds, no diagnosis, clear disclaimers

## Repository Structure
- `docs/` requirements and design documents

## Status
Week 3: requirements analysis.

## Author
[venkatesh]
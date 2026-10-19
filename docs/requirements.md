# Requirements Specification

**Project:** WhatsApp Health Assessment Assistant
**Problem Statement:** Meta Edge AI Challenge, Problem Statement 1
**Author:** [Your name]
**Version:** 0.2 (Week 3)

## 1. Purpose

An on-device multimodal AI assistant for Arm-based Android phones. The user sends an image and/or a text question about their health. The assistant combines computer vision and a Llama language model to give safe, general health guidance. The reply is shared back through WhatsApp.

## 2. Health Modules

| Module | Input | What it does | Priority |
|--------|-------|--------------|----------|
| M1 Nutrition | Meal photo + question | Identifies the food and gives general nutrition guidance | Must |
| M2 General health Q&A | Text question | Llama answers general health awareness questions | Must |
| M3 Medication label reader | Photo of a medicine box + question | Reads the medicine name and gives general information only | Could |
| M4 Health diary | Text notes | Summarises the user's daily health notes | Could |

## 3. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR1 | The user can provide an image (camera, gallery or WhatsApp share). | Must |
| FR2 | The user can enter a text question. | Must |
| FR3 | The system analyses the image with a computer vision model and reports a confidence score. | Must |
| FR4 | The system combines the image result and the question to generate contextual health guidance using Llama. | Must |
| FR5 | If confidence is below a threshold, the system says it is unsure and does not guess. | Must |
| FR6 | The system returns the response so it can be sent back through WhatsApp. | Must |
| FR7 | Every response shows a disclaimer: general information, not medical advice. | Must |
| FR8 | The system refuses to diagnose illness or recommend treatment or doses. | Must |
| FR9 | The user can view a history of previous questions and responses. | Could |

## 4. Non-Functional Requirements

| ID | Requirement | Target |
|----|-------------|--------|
| NFR1 | On-device inference: models run on the phone using ExecuTorch. | No server for inference |
| NFR2 | Performance: end-to-end response time on a mid-range Arm Android phone. | Initial goal under 10 s (to be measured) |
| NFR3 | Resource use: memory and storage fit a mid-range phone. | To be measured |
| NFR4 | Privacy: images and questions are not uploaded outside the device. | No external transmission |
| NFR5 | Safety: no diagnosis, dosing or treatment advice. | Enforced by a safety filter |
| NFR6 | Usability: a response in three steps or fewer. | Input, question, answer |

## 5. Constraints

- Required technologies: WhatsApp integration, Llama, ExecuTorch, a computer vision model, an Arm-based Android smartphone.
- Mandatory input modalities: image and text.
- Languages and tools: Python 3.10, Kotlin (Android), GitHub, GitHub Actions.

## 6. Out of Scope

- Medical diagnosis or treatment advice.
- Emergency detection or replacing a doctor.
- Accounts, cloud sync and multi-user features.

## 7. Assumptions

- The phone has enough memory for a small quantised model.
- Public datasets (for example Food-101) are enough to train the vision model.

## 8. Risks

| Risk | Mitigation |
|------|------------|
| ExecuTorch setup or export problems | Run a minimal example early |
| Llama too slow or large on the phone | Use a small quantised model and measure early |
| Too much scope for one person | Build M1 and M2 first; M3 and M4 only if time allows |
| Unsafe health answers | Safety filter, disclaimer and refusal rules |
| WhatsApp integration limits | Use the Android share/reply flow, confirmed with the lecturer |
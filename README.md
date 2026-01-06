# PJBL Feedback Analyzer

🔗 **Online Demo:** https://pjbl-feedback.online/

This repository contains the implementation of a **Project-Based Learning (PjBL) feedback analysis system** designed to analyze interaction messages exchanged within student project teams.

The system automatically detects:
- **Feedback category** (e.g., task-related, coordination, evaluation)
- **Feedback type** (positive, negative, neutral)
- **Feedback intent** (suggestion, critique, encouragement, clarification, etc.)

The objective is to support research on **collaborative learning, feedback dynamics, and learner regulation** by providing a reproducible analysis framework.

---

## Project Structure

pjbl-feedback-analyzer/
├── agent/              # Core analysis logic and agents
├── scripts/            # Model training and evaluation scripts
├── UI/                 # User interface (prototype/demo)
├── models/             # Generated model storage (created during training)
├── requirements.txt    # Python dependencies
└── README.md           # This file


---

---

⚡ Quick Start
Installation

    Clone the repository:

bash

git clone https://github.com/amal-phd/PjBL-feedback.git
cd pjbl-feedback-analyzer

    Install dependencies:

bash

pip install -r requirements.txt

    Run the demo application:

bash

cd UI
streamlit run UI/app.py    

🤖 Models
Model Availability

Trained models are not included in this repository due to size constraints. However, you can easily regenerate them using the provided training scripts.
Reproducing the Models

All models can be reproduced using the training scripts in the scripts/ directory. Executing these scripts will automatically generate the models locally under a models/ directory.
bash

# Train all models sequentially
python scripts/train_feedback_category_synth.py
python scripts/train_feedback_type_synth.py
python scripts/train_feedback_intent_synth.py

🔬 Research Context

This project is developed as part of academic research on:

Project-Based Learning in higher education

Feedback analysis and learning analytics

Collaborative learning dynamics

Learner regulation and metacognition

The repository accompanies a research paper and is provided to ensure reproducibility and transparency in educational technology research.


Data & Code Availability

Source Code: Fully available in this repository

Trained Models: Regenerable using provided scripts (excluded due to storage limits)

Training Scripts: Fully documented and reproducible

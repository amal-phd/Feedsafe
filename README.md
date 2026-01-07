PJBL Feedback Analyzer

🔗 Online Demo: https://pjbl-feedback.online/

Overview

This repository provides a research-oriented implementation of a feedback analysis system for Project-Based Learning (PjBL) environments.
The system is designed to analyze interaction messages exchanged within student project teams in online and blended learning contexts.

Feedback analysis is formalized as a set of supervised natural language classification tasks, enabling the automatic identification of multiple complementary dimensions of feedback.
The repository is intended to support empirical research, methodological transparency, and reproducible experimentation in learning analytics and educational AI.

Feedback Analysis Tasks

Each interaction message is analyzed along three independent dimensions:

1. Feedback Category

Multi-class classification into one of the following categories:

work_evaluation

revision_request

task_coordination

deadline_management

idea_proposal

clarification_request

decision_assertion

social_interaction

others

2. Feedback Type

positive

negative

neutral

3. Feedback Intent

constructive

harmful

neutral

These dimensions are modeled independently to preserve analytical interpretability and support fine-grained research analysis.

Research Objectives

The primary objective of this project is to support research on:

Collaborative learning processes in PjBL settings

Feedback dynamics within student teams

Learner regulation and interaction quality

Hybrid AI systems combining statistical models and symbolic rules

The system is designed with a strong emphasis on reproducibility, explainability, and controlled decision logic, making it suitable for experimental validation and extension.

System Architecture

The system follows a hybrid, modular, layered architecture, allowing each component to be evaluated or reused independently.

Layered Design
1. Dataset Layer

Structured interaction messages stored in JSONL format

One message per line

Fixed and reproducible train/validation/test splits

2. Model Layer

Three independently trained DeBERTa-based classifiers

One classifier per analytical dimension:

Feedback type

Feedback category

Feedback intent

Identical preprocessing and encoder architecture across tasks

3. Decision Layer (Agent + Rules)

A hybrid inference layer combining:

Statistical predictions from the trained classifiers

Explicit rule-based logic encoding domain knowledge and safety constraints

This layer is responsible for:

Aggregating model outputs

Interpreting combinations of predictions

Flagging potentially problematic feedback

Ensuring controlled and explainable decision-making

4. UI Layer

A Streamlit-based interface

Directly connected to the decision layer

Enables interactive, message-level analysis for research and demonstration purposes

Project Structure
pjbl-feedback/
├── data/
│   ├── clean_dataset_pjbl_feedback.jsonl   # Cleaned dataset (JSONL)
│   └── splits/
│       ├── train.jsonl
│       ├── valid.jsonl
│       └── test.jsonl
│
├── src/
│   ├── split_dataset.py        # Dataset splitting (JSONL)
│   └── train_all_tasks.py      # Unified training script (3 tasks)
│
├── agent/                      # Decision layer (models + rules)
├── UI/                         # Streamlit interface (connected to agent)
│
├── models/                     # Trained model checkpoints (generated locally)
├── requirements.txt            # Python dependencies
└── README.md                   # Project documentation

Installation

Clone the repository:

git clone https://github.com/amal-phd/PjBL-feedback.git
cd PjBL-feedback


Create and activate a virtual environment (recommended):

python -m venv .venv
source .venv/bin/activate      # Linux / macOS
.venv\Scripts\Activate.ps1     # Windows


Install dependencies:

python -m pip install -r requirements.txt


Dataset Preparation

All data handling is performed in JSONL format.

To generate reproducible train/validation/test splits:

python src/split_dataset.py


This produces:

data/splits/
├── train.jsonl
├── valid.jsonl
└── test.jsonl

Model Training

Three classifiers are trained independently, each formulated as a sequence classification task using the same encoder architecture (DeBERTa-v3) and consistent preprocessing.

Run the unified training script:

python src/train_all_tasks.py


This script sequentially trains and saves:

Feedback Type classifier

Feedback Category classifier

Feedback Intent classifier

Generated models are stored locally under:

models/
├── deberta_feedback_type/
├── deberta_feedback_category/
└── deberta_intent/

Reproducibility and Model Availability

Trained model weights are not included due to size constraints

All models can be fully reproduced using the provided scripts

Dataset splits are fixed and deterministic

Preprocessing and training procedures are consistent across tasks

Running the System (UI + Agent)

The repository includes a Streamlit-based research prototype directly connected to the decision layer.

Execution Flow

The user submits a feedback message via the UI

The agent performs inference using the trained classifiers

Model predictions are combined with rule-based decision logic

The structured analysis is returned to the UI

Run the system from the project root:

streamlit run UI/app.py

This design supports independent verification and replication of experimental results.

Research Context and Scope

This repository contributes to research on:

Project-Based Learning (PjBL) in higher education

Feedback analysis and learning analytics

Collaborative learning and group regulation

Hybrid AI systems combining models and rules

Communicative and metacognitive aspects of feedback

The repository accompanies an academic publication and is shared to promote open, transparent, and reproducible research.

Data and Code Availability

Source code: Fully available in this repository

Dataset: Provided in JSONL format

Models: Regenerable locally using provided scripts

Decision logic: Implemented in the agent layer (models + rules)

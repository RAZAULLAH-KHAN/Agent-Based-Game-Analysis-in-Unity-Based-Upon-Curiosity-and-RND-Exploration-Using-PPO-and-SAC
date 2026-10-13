# Agent-Based Game Analysis in Unity Based Upon Curiosity and RND Exploration Using PPO and SAC

## Overview
This repository contains the Final Year Project (FYP) work investigating reinforcement learning (RL) agents in Unity environments. The project trains and analyzes game agents using **Unity ML-Agents**, providing an empirical comparison between **Proximal Policy Optimization (PPO)** and **Soft Actor-Critic (SAC)** across three distinct exploration styles:
1. **Baseline** (Extrinsic reward only, no intrinsic exploration bonus)
2. **Curiosity** (Next-state prediction error via Intrinsic Curiosity Module)
3. **Random Network Distillation (RND)** (Exploration bonus via prediction error of a fixed random target network)

This establishes a six-condition experimental matrix in the **Hummingbirds** environment, followed by selected validation comparisons in a second game environment.

---

## Experimental Setup & Matrix

| Algorithm | Baseline | Curiosity (ICM) | Random Network Distillation (RND) |
| :--- | :---: | :---: | :---: |
| **PPO** | Condition 1 | Condition 2 | Condition 3 |
| **SAC** | Condition 4 | Condition 5 | Condition 6 |

- **Primary Environment:** Hummingbirds
- **Transfer / Validation Environment:** Second Unity Game Environment

---

## Evaluation Metrics
- **Extrinsic Cumulative Return (Primary Metric):** Performance and reward obtained directly from the game task.
- **Task Progress:** Domain-specific completion and milestone metrics.
- **Exploration Coverage:** State/spatial coverage diagnostics during training.
- **Statistical Validity:** All training conditions repeated across multiple random seeds to account for stochastic variation.

---

## Planned Deliverables (Objective 4)
- **Trained Unity Agents:** Two Unity games featuring fully trained reinforcement learning agents.
- **Code & Configuration Settings:** Source code, environment wrappers, and ML-Agents YAML configuration files.
- **Weights & Biases (W&B) Dashboard:** Experiment tracking logs, training metrics, and comparative evaluation graphs.
- **Final Research Report:** Comprehensive documentation covering experimental methodology, comparative analysis, and findings.

---

## Tools & Technologies
- **Game Engine & Environment:** Unity, C#
- **Reinforcement Learning Framework:** Unity ML-Agents, Python, PyTorch
- **Experiment Tracking & Analysis:** Weights & Biases (W&B)
- **Version Control:** Git & GitHub

---

## Project Timeline
- **Duration:** 8 Months

---

## Project Team & Supervision
- **Student Researcher:** Raza Ullah Khan (bscs23f28@namal.edu.pk)
- **Supervisor:** Dr. Malik M Ali Shahid
- **Co-Supervisor:** Mr. Abdul Rafay
- **Industrial Partner:** Inspired Square

---

## Repository Structure
```
unity-rl-exploration-ppo-sac/
├── README.md
├── docs/           # Proposal documents, slides, and reports
│   ├── proposal_details.docx
│   ├── proposal_presentation.pptx
│   └── updated_fyp_proposal.docx
└── .gitignore
```

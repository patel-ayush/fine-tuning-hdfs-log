# 🔥 Synthetic Log Distillation: Because Regex is a Nightmare

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/10M9tK8gFJYjLKr4eavL5IZo4qkrvxtzd?usp=sharing)

Welcome to the **"I refuse to write another RegEx"** pipeline. 

This project is a production-ready demonstration of **Knowledge Distillation**—aka "Getting the Intern (Llama 3.1 8B) to do the work of the Senior Engineer (Qwen 3) for fraction of the cost."

## 🧐 The Problem: "Log Drift"
You know the drill.
1.  DevOps Dave changes a log format from `[INFO] User 123` to `INFO: User 123`.
2.  Your 400-line Regex parser explodes.
3.  You get paged at 3 AM.
4.  You cry.

**Traditional Solution:** maintain a regex that looks like `^(\d{4}-\d{2}-\d{2})\s+([A-Z]+)...` (it’s ugly, admitted).
**Our Solution:** Just ask an LLM. But wait! LLMs are slow and expensive! 😱

## 💡 The Solution: Teacher-Student Distillation
We use a **Big Brain Model (Teacher)** to label data, and a **Speedy Boi Model (Student)** to learn the pattern.

1.  **Teacher (Qwen 3)**: "I have read the entire internet. I know what a JSON is. I will carefully format this log for you."
2.  **Student (Llama 3.1 8B)**: "I have no idea what's happening, but I see you outputting JSONs, so I'm gonna do that too." -> **And it works.**

We use **QLoRA** (Quantized Low-Rank Adaptation) because we are poor and only have free Colab GPUs.

## 🚀 How to Run this Thing
Don't just star the repo, actually run it.

1.  **Click the "Open in Colab" badge**.
2.  **API Keys**: You need `HF_TOKEN` (Hugging Face) access to Llama 3.1. If you don't have it, go ask Mark Zuckerberg nicely (or just click "Accept" on the model page).
    *   Set it in **Colab Secrets** (that little key icon on the left).
    *   `WANDB_API_KEY` is optional, but highly recommended if you like pretty graphs.
3.  **Run All Cells**. Go get a coffee. Come back to a trained model.

## ⚙️ Config (For the Tinkerers)
At the top of the notebook, there's a `CONFIG` dict.
*   Want to use your own logs? Change `DATA_FILE`. You can also use the dataset from `data/HDFS_2k.log`.
*   Want to use a different Teacher? Change `TEACHER_MODEL`.
*   Want to break everything? Change `learning_rate` to `1.0`.

## 🔮 Roadmap
*   [ ] Make it work with 100k lines (RIP Colab RAM).
*   [ ] Export to GGUF so I can run it on my toaster (Raspberry Pi).
*   [ ] Automated "Complaint Generation" when logs are too messy.

## 📜 License
MIT. Do whatever you want, just don't blame me if your production cluster catches fire.

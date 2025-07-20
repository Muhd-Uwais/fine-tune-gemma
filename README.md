# 🔧 Fine-Tuning Gemma-3B-IT with Hugging Face + llama.cpp

This project demonstrates how to fine-tune [Gemma-3B-IT](https://huggingface.co/google/gemma-3b-it) using Hugging Face Transformers with PEFT, LoRA, and BitsAndBytes for efficient training. The final model is converted to **GGUF** format for local inference using `llama.cpp`.

---

## 📚 Learning Objectives

By following this project, you will learn:

- How to fine-tune LLMs using PEFT (LoRA) and 4-bit quantization
- How to prepare a custom dataset for supervised fine-tuning (SFT)
- How to use `trl.SFTTrainer` for efficient training
- How to merge adapters into a full model
- How to convert to GGUF format for `llama.cpp`

---

## ⚙️ Installation

Install required packages:

```bash
pip install bitsandbytes peft trl accelerate datasets transformers
```

---

## 🚀 Quickstart

### 1. Login to Hugging Face

```python
from huggingface_hub import notebook_login
notebook_login()
```

---

### 2. Prepare Your Dataset

Your dataset should be in `.jsonl` format like this:

```json
{"instruction": "Turn on the light", "context": "Sure, the light is now on."}
```

---

### 3. Run Fine-Tuning

Use the `trl.SFTTrainer` with PEFT LoRA to fine-tune the model.

📘 Full training code available in [`fine_tune_gemma.ipynb`](fine_tune_gemma.ipynb)

---

### 4. Merge LoRA + Convert to GGUF

After training and merging LoRA weights:

```bash
python3 convert_hf_to_gguf.py merged_model/ --outfile gemma3.gguf
./llama.cpp/build/bin/llama-quantize gemma3.gguf lumina-gemma3-q4.gguf q4_0
```

---

### 5. Inference with llama.cpp

Use your quantized `.gguf` model locally via `llama.cpp`.

---

## 📬 Contact

For feedback or questions, [Contact Me](https://nox-uwi.github.io/Form/)

If you want to improve this project or suggest better code, feel free to **open a pull request** or contact me with your ideas!

---

## 🌟 Star this project if it helped you!


> Built with ❤️ and 🧠 by an aspiring AI Developer

---

Happy Coding! 🚀

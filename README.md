# 🧠 LLM Prompt Engineering Basics

Learn the fundamentals of designing **cost-efficient**, **goal-oriented**, and **production-ready** prompts to get the best out of LLMs like OpenAI, DeepSeek, Gemini, and others.

---

## 📌 Description

This repository focuses on the **Fundamentals of Prompt Engineering**, including:

- **Prompt Optimization**
- **Zero-Shot, Few-Shot, and Chain of Thought (CoT) Prompting**
- **Token Cost Reduction Strategies**
- Real-world example: **Generating Kubernetes Manifests using Prompts**

---

## 📚 Table of Contents

- [Problem Statement](#-problem-statement)
- [Solution Architecture](#-solution-architecture)
- [Prompting Techniques](#-prompting-techniques)
  - [Zero-Shot Prompting](#zero-shot-prompting)
  - [Few-Shot Prompting](#few-shot-prompting)
  - [Multi-Shot Prompting](#multi-shot-prompting)
  - [Chain of Thought (CoT)](#chain-of-thought-cot)
- [Prompt Cost Optimization](#-prompt-cost-optimization)
- [Examples](#-examples)
- [Best Practices](#-best-practices)
- [Resources](#-resources)
- [License](#-license)

---

## ❓ Problem Statement

Create a **Python-based solution** that can:

> **Generate YAML manifests (Deployment, Service, etc.) using LLMs based on user input.**

---

## 💡 Solution Architecture

1. **Accept user input** (e.g., `deployment`, `service`)
2. **Prepare an optimized prompt**
3. **Call LLM API (OpenAI, DeepSeek, etc.)**
4. **Receive and display concise YAML output**

> ⚠️ Note: LLM API calls are **not free** — the better the prompt, the **lower the cost**.

---

## 🌟 Prompting Techniques

### ✅ Zero-Shot Prompting

- Direct command without examples.
- Works best with **common or well-known tasks**.

**Example:**

```text
Generate a shell script to fetch Docker version.
```

---

### ✅ Few-Shot Prompting

- Include 1–2 examples before the final prompt.
- Helps align output to **organization standards**.

**Example:**

```text
Example 1:
Fetch Docker Version:
#!/bin/bash
# Author: Madhav Wakhare
# Version: v1
docker --version

Example 2:
Fetch Terraform Version:
#!/bin/bash
# Author: Madhav Wakhare
# Version: v1
terraform --version

Now, Fetch versions of all installed processes.
```

---

### ✅ Multi-Shot Prompting

- More examples = more accurate & relevant responses.
- Use when task is complex or domain-specific.

---

### ✅ Chain of Thought (CoT)

- Step-by-step reasoning embedded into prompt.
- Useful for **logical**, **multi-step**, or **explanatory** tasks.

---

## 💰 Prompt Cost Optimization

- LLM API pricing is based on **tokens**, not words.
- Example:
  - Gemini: \~100 words ≈ 60–80 tokens
- **Bad Prompt**:\
  `Generate a Kubernetes manifest file for Deployment Resource.`
- **Good Prompt**:\
  `Generate ONLY Kubernetes manifest file for Deployment Resource.`

🔪 **Use Google AI Studio** to compare token costs between prompts.

---

## 🧪 Examples

### Prompt Engineering in Action

**Prompt**:

```
Generate ONLY Kubernetes manifest file for Deployment Resource.
```

**Output**:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.25
          ports:
            - containerPort: 80
```

---

## ✅ Best Practices

1. **Provide Context**

   > What are you doing? What is the goal?

2. **Give Clear Instructions**

   > What exactly do you want as output?

3. **Add Examples**

   > Show how you want the answer structured.

4. **Specify Output Format**

   > E.g., “Please provide output in `.md` or `.yaml` format only.”

5. **Always keep prompts minimal but expressive.**

---

## 📚 Resources

- [OpenAI Cookbook](https://github.com/openai/openai-cookbook)
- [Prompt Engineering Guide](https://github.com/dair-ai/Prompt-Engineering-Guide)
- [Google AI Studio](https://aistudio.google.com/app/prompts)

---

## �� License

This project is licensed under the [MIT License](LICENSE).


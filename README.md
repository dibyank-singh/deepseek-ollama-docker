# 🚀 DeepSeek Coder with Ollama - Docker Setup  

This repository provides a **Docker Compose** setup to run **DeepSeek Coder** using **Ollama** on your local machine. It simplifies the process of setting up and using **DeepSeek Coder**, a powerful AI model for code generation.

---

## 📌 What is DeepSeek Coder?
[DeepSeek Coder](https://ollama.com/library/deepseek-coder) is an advanced AI model trained on **2 trillion tokens** of code and natural language. It supports:
- ✅ **Multiple model sizes**: 1.3B, 6.7B, 33B parameters  
- ✅ **High-quality code generation**  
- ✅ **Support for multiple programming languages**  

---

## 📌 How It Works
This setup uses **Ollama**, an open-source model runner, to serve **DeepSeek Coder** inside a **Docker container**. You can interact with it via CLI, API, or Python.

---

## 🚀 Getting Started

### 1️⃣ **Clone the Repository**
```sh
git clone https://github.com/YOUR_USERNAME/deepseek-ollama-docker.git
cd deepseek-ollama-docker
```
### Run the Containers
#### Make sure you have Docker installed, then start the service:
```sh
docker-compose up -d
```
This will:

✅ Pull the latest Ollama image
✅ Run the container on port 11434
✅ Persist downloaded models in a Docker volume

#### To check if the container is running:
```sh
docker ps
```

## 🛠 Using DeepSeek Coder
3️⃣ Pull a DeepSeek Model
Once the container is running, enter it:
```sh
docker exec -it ollama_service bash
```
Inside the container, pull a model:
```sh
ollama pull deepseek-coder
```
(For a larger model: ollama pull deepseek-coder:6.7b or ollama pull deepseek-coder:33b)

## 4️⃣ Run DeepSeek Coder
After downloading, you can start it:
```sh
ollama run deepseek-coder
```

## 🔥 API Access
You can send requests to the API running on http://localhost:11434.

Example using curl:
```sh
curl -X POST http://localhost:11434/api/generate -d '{
  "model": "deepseek-coder",
  "prompt": "Write a Python function that uses matplotlib to plot a graph of y = x^2."
}'
```
#### Example using Python:
```sh
import requests

url = "http://localhost:11434/api/generate"
data = {
    "model": "deepseek-coder",
    "prompt": "Write a Python function that uses matplotlib to plot a graph of y = x^2."
}

response = requests.post(url, json=data)
print(response.json())
```

## 🛑 Stopping & Restarting
Stop the containers:
```sh
docker-compose down
```
#### Restart the containers:
```sh
docker-compose up -d
```


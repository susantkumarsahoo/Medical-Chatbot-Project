# Medical-Chatbot-Project

A Medical Chatbot Project involves developing an AI-powered conversational agent designed to provide users with accessible and reliable medical information and support.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Tech Stack](#tech-stack)
3. [Setup & Installation](#setup--installation)
4. [Environment Variables](#environment-variables)
5. [Running the Project](#running-the-project)
6. [AWS Deployment](#aws-deployment)
7. [Policies & Permissions](#policies--permissions)
8. [GitHub Secrets](#github-secrets)

---

## Project Overview
This project implements a medical chatbot using AI and NLP technologies. It leverages LangChain, GPT models, and Pinecone for embeddings storage, allowing real-time responses to user queries. The project is designed to be deployable on AWS using EC2 and Docker with CI/CD via GitHub Actions.

---

## Tech Stack
- **Programming Language:** Python  
- **Frameworks & Libraries:** LangChain, Flask, GPT  
- **Database / Vector Storage:** Pinecone  
- **Deployment:** AWS EC2, Docker, GitHub Actions (CI/CD)  

---

## Setup & Installation

### Step 1: Clone the Repository
```bash
git clone <YOUR_REPO_URL>
cd Medical-Chatbot-Project


--

## Step 2: Create Conda Environment
conda create -n medibot python=3.10 -y
conda activate medibot

## Step 3: Install Dependencies
pip install -r requirements.txt

## Step 4: Configure Environment Variables

Create a .env file in the root directory and add your credentials:

PINECONE_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

## Running the Project
Step 1: Store Embeddings in Pinecone
python store_index.py

Step 2: Launch the Application
python app.py


Open your browser and go to http://localhost:5000 (or the port your Flask app is running on).

AWS Deployment
Step 1: Login to AWS Console

Create IAM user with required access.

Step 2: EC2 & ECR Setup

EC2: Virtual machine for deployment

ECR: Elastic Container Registry to store Docker images

Step 3: Docker Setup on EC2 (Ubuntu)
sudo apt-get update -y
sudo apt-get upgrade -y
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker

Step 4: Build & Push Docker Image
docker build -t medibot .
docker tag medibot:latest 315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot:latest
docker push 315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot:latest

Step 5: Run Docker Image on EC2
docker pull 315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot:latest
docker run -d -p 5000:5000 medibot:latest

Policies & Permissions

AmazonEC2ContainerRegistryFullAccess

AmazonEC2FullAccess

Create ECR repository and save the URI:
315865595366.dkr.ecr.us-east-1.amazonaws.com/medibot

GitHub Secrets

Add the following secrets in your GitHub repository:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

AWS_DEFAULT_REGION

ECR_REPO

PINECONE_API_KEY

OPENAI_API_KEY











# 📧 Automated Cold Email Generator
This project is an automated tool that generates personalized cold emails by scraping job descriptions from the web and matching them with a portfolio of relevant projects stored in a vector database. It leverages a LangChain pipeline to connect different components, including a Large Language Model (LLM) and a ChromaDB vector store.

## ✨ Features
**Intelligent Web Scraping**: Automatically extracts key information (role, experience, skills, description) from job postings on a given URL using the WebBaseLoader function from langchain_community.

**Vector-Based Portfolio Matching**: Uses a vector database (ChromaDB) to find the most relevant projects from your portfolio (my_portfolio.csv) based on the skills required in the job description.

**AI-Powered Email Generation**: Crafts a professional cold email tailored to the job posting, incorporating your company's profile and the most relevant portfolio links.

**Robust Data Handling**: The system is designed to handle and parse structured data from the LLM using Pydantic models, ensuring reliable JSON output.

## ⚙️ How It Works
The core of the application is a multi-step LangChain pipeline:

**Job Posting Extractio**n: A LangChain LLM is given the scraped text from a job posting URL and an instruction to extract specific details (role, experience, skills, description) into a structured JSON format. This is made reliable by using Pydantic models to enforce the output schema.

**Portfolio Retrieval**: The extracted skills from the job posting are used to query a ChromaDB vector store. This store contains embeddings of project tech stacks from your my_portfolio.csv file. The top 2 most relevant portfolio links are retrieved.

**Email Composition**: A final LLM call is made with a detailed prompt that includes the extracted job description and the relevant portfolio links. The LLM acts as a business development executive (Mohan) and writes a personalized cold email.

## 🚀 Setup & Usage
Prerequisites
Python 3.8+

A Google or Groq API key for the LLM.

Your portfolio data in a CSV file named ```my_portfolio.csv``` with "Techstack" and "Links" columns.

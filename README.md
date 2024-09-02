# GenAI-Project-Email-Generator-for-Job-url
# Cold Email Generator

![image](https://github.com/user-attachments/assets/d685f98f-5f95-41e8-8143-a35b686d7c7f)


## Overview

This project is a cold email generator that takes a job URL as input and generates a personalized email content by matching suitable portfolios from a database. The project leverages Groq for faster inference and uses various tools and libraries to extract job details, store embeddings, and generate emails.

## Architecture

!Project Architecture

The architecture of the project is as follows:
1. **Career's Page**: The source of job listings.
2. **Extracted Jobs in JSON Format**: Jobs are extracted with fields such as title, skills, experience, and description.
3. **Job**: The job details are processed.
4. **LLM (Large Language Model)**: Used to generate the email content.
5. **Cold Mails**: The final output, which is the generated email.
6. **Portfolio Links**: Links to suitable portfolios.
7. **Vector Store**: Stores embeddings of portfolios for quick retrieval.

## Setup

### Prerequisites

1. **Groq Account**: Create an account at Groq Console and generate an API key.
2. **Python Environment**: Ensure you have Python installed.

### Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/your-repo/cold-email-generator.git
    cd cold-email-generator
    ```

2. Create a virtual environment:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

4. Set up environment variables:
    - Create a `.env` file in the root directory.
    - Add your Groq API key:
        ```
        GROQ_API_KEY=your_groq_api_key
        ```

### Requirements

Create a `requirements.txt` file with the following content:
langchain==0.2.14 langchain-community==0.2.12 langchain-groq===0.1.9 unstructured==0.14.6 selenium==4.21.0 chromadb==0.5.0 streamlit==1.35.0 pandas==2.0.2 python-dotenv==1.0.0


### Usage

1. **Extract Job Details**:
    ```python
    from langchain_community.document_loaders import WebBaseLoader

    loader = WebBaseLoader("job_url")
    job_details = loader.load()
    ```

2. **Generate Email Content**:
    ```python
    from langchain_groq import ChatGroq

    llm = ChatGroq(
        temperature=0,
        groq_api_key='your_groq_api_key',
        model_name="llama-3.1-70b-versatile"
    )
    response = llm.invoke("The first person to land on moon was ...")
    print(response.content)
    ```

3. **Store Portfolios in VectorDB**:
    ```python
    import chromadb

    # Code to store embeddings in chromadb
    ```

4. **Run Streamlit App**:
    ```bash
    streamlit run app.py
    ```

### Challenge

During the environment setup, there was an issue with installing `chromadb` as it required Microsoft C++ Build Tools. This was resolved by installing the necessary build tools.

## References

- Groq Console
- Python Dotenv
- ChromaDB Documentation
- LangChain Community Web Scraper


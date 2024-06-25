# Custom RAG Pipeline with Streamlit and FastAPI

This repository contains a custom Retrieval-Augmented Generation (RAG) pipeline implemented using Streamlit for the frontend and FastAPI for the backend. The application allows users to upload PDF documents, generate embeddings, and ask questions about the content, receiving contextually relevant responses.

## Features

- **PDF Upload and Processing**: Upload a PDF file and process it to extract text.
- **Embeddings Generation**: Generate embeddings for document chunks using a pre-trained transformer model.
- **Question Answering**: Ask questions about the document and get answers based on the document content.
- **Dockerized Application**: The entire application runs within a Docker container for easy deployment.

## Architecture

![Architecture Diagram](Architecture_Diagram.png)  <!-- Add the path to your architecture diagram here -->

1. **User**: Interacts with the Streamlit frontend.
2. **Streamlit App**: Provides UI for uploading PDFs and asking questions.
3. **FastAPI App**: Handles API requests for question answering.
4. **Embedder Model**: Generates embeddings for the documents, queries and does cosine similarity search.
5. **Generator Model**: Generates responses based on the context and user query.
6. **Docker Container**: Encapsulates the entire application environment.

## Setup Instructions

### Prerequisites

- Python 3.7 or higher
- pip (Python package installer)

### Installation

1. **Clone the repository:**
    ```sh
    git clone https://github.com/Viksam/CustomRAGpipeline.git
    cd CustomRAGpipeline
    ```

2. **Create and activate a virtual environment (recommended):**
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install the required packages:**
    ```sh
    pip install streamlit torch transformers llama-cpp sklearn pymupdf
    ```

### Usage

1. **Run the Streamlit app:**
    ```sh
    streamlit run main.py
    ```

2. **Open the provided URL in your web browser (usually http://localhost:8501).**

3. **Interact with the application:**
    - Upload a PDF file.
    - Enter a question related to the content of the PDF.
    - Receive a response generated based on the document content.

      **Example**
     <img src="Example.png" width="500" title="Example">

4. **Common Errors:**
    - Numpy error while running Torch's tensor operations.
        - if you are using Numpy 2.0.0 version you might get this error. Downgrade your Numpy version to 1.26.4 or lower.
        ```sh
         pip install numpy==1.26.4
        ```
    - CMAKE error while installing llama_cpp.
        - This will happen most likely to Windows users. Please refer to the below link.
        - https://github.com/abetlen/llama-cpp-python?tab=readme-ov-file#installation-configuration

### Dependencies

- `streamlit`: For building the interactive web application.
- `torch`: For PyTorch functionalities.
- `transformers`: For handling the transformer models from HuggingFace.
- `llama-cpp`: For working with the GGUF Models.
- `scikit-learn`: For computing cosine similarity.
- `pymupdf`: For loading and processing PDF files.


## Demo

### 1. Colab Notebook:
#### Prerequisites

- Colab with atleast T4 GPU runtime.

https://colab.research.google.com/drive/1Ge7TtSJ9ZgOuKQHHBx7jZ6Hc2VxGIOi_?usp=sharing


### 2. Docker Image:
#### Prerequisites

- Docker installed on your system.

#### Pull Docker Image

You can pull the pre-built Docker image from GitHub Packages using the following command:

```bash
docker pull ghcr.io/viksam/customragpipeline:latest

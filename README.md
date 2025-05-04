# Medical RAG QA App

This project implements a **Medical RAG (Retrieval-Augmented Generation) QA Application** using the **Meditron 7B LLM**, **Qdrant Vector Database**, and the **PubMedBERT Embedding Model**. The app provides efficient and accurate answers to medical-related questions by retrieving relevant data and augmenting it with powerful language model generation.

## Table of Contents

* [Project Overview](#project-overview)
* [Key Components](#key-components)
* [Setup Instructions](#setup-instructions)
* [How it Works](#how-it-works)
* [Usage](#usage)
* [Contributing](#contributing)
* [License](#license)

## Project Overview

This project is designed to create a medical Q\&A application that leverages the power of Retrieval-Augmented Generation (RAG) to provide answers to complex medical queries. By integrating the **Meditron 7B Language Model**, **Qdrant Vector Database** for efficient vector search, and the **PubMedBERT** embedding model, the app ensures accurate, contextually relevant, and scientifically grounded answers.

## Key Components

1. **Meditron 7B LLM**: A large language model capable of generating human-like text. It is used for generating answers to medical questions once the relevant data has been retrieved from the database.

2. **Qdrant Vector Database**: A vector search engine that stores and retrieves embeddings efficiently. It is used to store medical documents and find the most relevant ones based on query embeddings.

3. **PubMedBERT**: A variant of BERT fine-tuned on the PubMed dataset. It is used for embedding medical documents and queries into high-dimensional vectors, allowing the system to perform semantic search.

## Setup Instructions

Follow these steps to set up the project locally:

### Prerequisites

* Python 3.x
* Pip (Python package installer)
* Docker (optional for database containerization)
* Access to Qdrant Vector Database API

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/Medical-RAG-using-Meditron-7B-LLM.git
   cd Medical-RAG-using-Meditron-7B-LLM
   ```

2. Create a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate  # For Linux/macOS
   venv\Scripts\activate     # For Windows
   ```

3. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Set up the Qdrant Vector Database. If you are using Docker, you can start a Qdrant instance:

   ```bash
   docker run -p 6333:6333 qdrant/qdrant
   ```

5. (Optional) Download the PubMedBERT model and Meditron 7B LLM model. You can follow the instructions in the documentation of each model to obtain these files.

### Configuration

Edit the configuration file (`config.yaml`) to include the correct paths to your models and Qdrant database connection details.

```yaml
qdrant_host: "http://localhost:6333"
pubmedbert_model_path: "path_to_pubmedbert_model"
meditron7b_model_path: "path_to_meditron7b_model"
```

## How it Works

1. **Query Embedding**: When a user submits a medical question, the query is first embedded using **PubMedBERT**, which converts the question into a high-dimensional vector.

2. **Document Retrieval**: The query vector is then sent to the **Qdrant Vector Database**, which performs a semantic search to find the most relevant medical documents.

3. **Answer Generation**: The retrieved documents are passed to the **Meditron 7B LLM** for generating a coherent and contextually appropriate answer based on the retrieved information.

4. **Answer Display**: The generated answer is presented to the user in a readable format.

## Usage

Once the system is set up, you can run the application by executing the following command:

```bash
python app.py
```

The app will start a local web server, and you can interact with it through a web interface or via API calls.

### Example Query

Submit a medical question such as:

> *"What are the symptoms of diabetes?"*

The system will search relevant PubMed documents, process them using the Meditron 7B LLM, and generate an answer.

## Contributing

If you'd like to contribute to the development of this project, feel free to fork the repository, create a new branch, and submit a pull request. Please ensure your code adheres to the existing style and includes appropriate tests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


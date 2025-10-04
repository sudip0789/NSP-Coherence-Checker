# Coherence Checker: A Multi-Approach Framework for Next Sentence Prediction
This is a multi-phase project designed to evaluate and improve sentence coherence using advanced NLP techniques. This repository explores fine-tuning, prompt engineering, and retrieval-augmented generation (RAG) to build a robust Next Sentence Prediction (NSP) tool, particularly aimed at assisting young children and non-native English speakers in constructing coherent sentences.

## Dataset: WikiParagraphs

The foundation of this project is the WikiParagraphs dataset, a large-scale collection of coherent and incoherent sentence pairs sourced from Wikipedia.
- Original Size: The dataset is massive, containing over 25 million training examples and 3 million for both validation and testing.
- Sampling for Feasibility: To ensure the project could be developed on standard computing resources, the dataset was sampled down to a more manageable size
  - Training: 70,000 pairs 
  - Validation: 15,000 pairs 
  - Testing: 15,000 pairs
    
If you have access to significant computational resources, you can modify the data preparation scripts to train the models on the full dataset for potentially higher performance.

## Project Architecture
This project was built in four main stages, systematically exploring different methods for Next Sentence Prediction (NSP)

1. Fine-Tuning BERT: A bert-base-uncased model was fine-tuned on the Wiki Paragraphs dataset to create a specialized NSP classifier. This achieved a baseline accuracy of 71.1%.

2. Prompt Engineering: A google/flan-t5-base model was tested using zero-shot (standard) and few-shot prompting. The few-shot approach proved superior, increasing accuracy from 51% to 56% by providing in-context examples.

3. Retrieval-Augmented Generation (RAG): A FAISS vector index was built to provide the model with external context. This method is highly dependent on the relevance of the retrieved documents.

4. Hybrid Tiered System: The final architecture combines the best models into an efficient, confidence-based pipeline.

  - Tier 1: The fast, fine-tuned BERT model makes the initial prediction.
  - Tier 2 (Fallback): If the confidence is low (<80%), the system passes the task to google/flan-t5-large model using a few-shot prompt for deeper reasoning.

## Key Features
- Multi-Model Evaluation: Compares the performance of fine-tuned BERT, prompt-based LLMs, and a RAG system.
- FAISS-Powered RAG: Implements a semantic search system to retrieve relevant context and enhance prediction accuracy.
- Intelligent Hybrid System: A tiered architecture that uses a fast model for easy cases and a powerful LLM for difficult ones.
- Interactive Demo: Allows users to input their own sentences and get instant coherence 

## Contributing
Contributions make the open-source community an amazing place to learn, inspire, and create. If you have a suggestion that would make this better, feel free to add to it. Any contributions you make are greatly appreciated.

1. Fork the Project
2. Create your Feature Branch (git checkout -b feature/AmazingFeature)
3. Commit your Changes (git commit -m 'Add some AmazingFeature')
4. Push to the Branch (git push origin feature/AmazingFeature)
5. Open a Pull Request

## Contact
**Sudip Das** - [LinkedIn](https://www.linkedin.com/in/sudip-das-40004817b/)

Project Link: https://github.com/sudip0789/NSP-Coherence-Checker

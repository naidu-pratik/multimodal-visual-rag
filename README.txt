Case-Based Visual Retrieval-Augmented Generation Framework for Clinical Decision Support

A multimodal clinical decision support system that generates grounded suggestive diagnostic impression for a chest x-ray using case-based retrieval and large language models

This project implements a Visual-RAG framework which retrieves historically similar x-rays and uses associated clinical text to generate suggestive diagnosis for a new unseen chest x-ray.


System Architecture
1. Knowledge Source Creation
- We use a pre-trained DenseNet-121 model to generate visual embeddings for chest x-rays.
- We use BioClinicalBERT to generate text embeddings for the associated clinical reports.
- We pair these embeddings using patient id and store them in FAISS index.

2. Retrieval Module
- Using the query chest x-ray, we retrieve top-k similar visual embeddings.
- We then fetch the associated textal report embeddings.
- We form groups from the retrieved report by performing re-ranking of the textual reports based on linguistic similarity
- Biggest group of similar reports make the evidence set.

3. Diagnosis Generation
- We provide the system prompt and user prompt.
- We provide evidence set along with the prompts to LLM(Chat-GPT 5)
- LLM generates a radiology-styled impression

4. Report Generation
- We take the query chest x-ray and the generated suggestive diagnosis.
- We use template for the report structure
- The final report contains basic patient information, x-ray and the generated diagnosis.



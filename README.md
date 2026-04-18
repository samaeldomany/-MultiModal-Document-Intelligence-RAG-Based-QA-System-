# -MultiModal-Document-Intelligence-RAG-Based-QA-System-
The project  aims to implement a Multimodal RAG system that can analyze and process complex financial documents that includes visuals, images and charts which is a more advanced approach than the standard text based RAG systems that only consider text chunks this system uses the ColPali model and Gemini API 

## System Architecture
The pipeline consists of three main stages:
1. Ingestion: PDF files are converted into images using the pdf2image library. 
2. Indexing: The system uses vidore/colpali-v1.3 to create multi vector embeddings for each page. These are stored in a Qdrant vector database using Late Interaction (MaxSim) to match query tokens to specific image patches.
3. Generation: When a query is made, the most relevant page image is retrieved and sent to Gemini 2.5 Flash. The model is prompted to answer strictly based on the provided image to prevent hallucinations.


## Evaluation
The system has been tested against:

- Federal Reserve Financial Stability Report (April 2024) https://drive.google.com/open?id=1pfTZ3hMLSWsKRKAbtn-cm3IfC5mXM0op&usp=drive_copy
- IMF Global Financial Stability Report (April 2024)https://drive.google.com/open?id=1BwcoOh_y_Kp2peL2P7IsmuZYlrHkuZnh&usp=drive_copy
- Central Bank of Egypt Financial Stability Report (March 2025)https://drive.google.com/open?id=1yIQ_lGbUgPXTzS9G1CEZf5CWIIK4E1Lg&usp=drive_copy

Benchmark tests confirmed accurate extraction of data from financial tables and visual trends from bar charts, as well as successful refusal to answer queries not present in the documents.

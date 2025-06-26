# Code-Irene Description  
In this python notebook five RAG query translation techniques have been defined: Naive, Decomposition (Indivudually and Recursively answered), RAG-Fusion, and HyDE.  
For the advanced techniques, the codes provided by LangChain in the repository https://github.com/langchain-ai/rag-from-scratch.git have been adapted in the context of airlines' sustainability reports.  

For the evaluation of these techniques, the RAGAs library has been used. Specifically, the three metrics Answer Correctness, Context Recall, and Faithfulness.  

At the beginning of the code an Embedding section is also present, a continuation of the work of Vishnu R. With this code, the chunked documents are embedded and stored in a .zip FAISS file, which can later be used as a database for the RAG system both in the evaluation of the different query translation techniques, and for the chatbot.

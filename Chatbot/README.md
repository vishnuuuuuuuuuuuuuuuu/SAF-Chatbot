# Chatbot Description  
This chatbot builds on the findings of Irene S. and Ernest K., made possible by the data preprocessing work by Vishnu R.. More specifically:  
- From Irene S.'s study, RAG-Fusion resulted as the best query translation technique to build an airlines' sustainability report chatbot, as it balances accuracy and time efficiency;
- From Ernest K.'s study, Evidence-Aware Few-Shot resulted as the best prompting technique in the same context, as it has the best average score over Answer Correctness, Context Recall, and Faithfulness.

The chatbot, built using Gradio library, merges RAG-Fusion and Evidence-Aware Few-Shot into a user-friendly tool.  

The FAISS index we used when testing the chatbot is at /Evaluation-Irene/faiss_27reports.zip, but other indexes can be used.  
New indexes can also be created using the code at /Vishnu pre-processing/SAF TPP code.py, and then Embedding part of the code found at Code-Irene/models_and_evaluation_irene.py.

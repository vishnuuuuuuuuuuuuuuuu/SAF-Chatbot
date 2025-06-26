# Intro
The original file including the metadata can be downloaded with Thesis_Ernest_K_w_Outputs, the secoond file "Thesis_Ernest_K_vanila" is for display of code within github environment. Please note, that after rerunning the code the outputs of the model are subject to change, hence expect a deviation in scores. 

# Uploading the documents
To run the code currectly you will need to upload both Ground_truth_fin_22-24 and Ground_truth_fin (this one is needed for template only). Additinoally you will need to upload faiss_index.zip to use the context reference.  
# Prompt testing pipeline 
Stage 1 – Initialization
The script begins by creating an empty list called results that will hold each question’s output and associated metadata.

Stage 2 – Iterating over examples
For every item in the ground_truth collection, it pulls out the field question and stores it in the variable q.

Stage 3 – Document retrieval
It calls retriever.invoke(q) to fetch relevant document excerpts. Each returned document’s filename, page number, and text are combined into a single string block separated by blank lines.

Stage 4 – Prompt assembly
A prompt list is built in four parts:
• A SystemMessage instructing the model to act as a “document analyst,” use only the provided excerpts, cite sources, and answer “I don’t know” if the answer is not found.
• A sequence of HumanMessage/SystemMessage pairs representing a few‐shot set of example questions and their correct answers.
• A HumanMessage containing the formatted “Retrieved documents” block.
• A final HumanMessage with the new question, prefixed by “Q: ”.

Stage 5 – Model invocation
The assembled prompt is sent to chat.invoke(...). The response object’s content is the model’s answer.

Stage 6 – Result recording
A dictionary is appended to results with keys:
model_id (“evidence_aware_fewshot”), question, answer (the model’s text), reference (the true answer), and contexts (the raw retrieved texts).

Stage 7 – Dataset creation
The list of result dictionaries is converted into a Dataset via Dataset.from_list(results).

Stage 8 – LLM wrapper
The chat model is wrapped in a LangchainLLMWrapper so it conforms to the evaluator’s expected interface.

Stage 9 – Evaluation
The script calls evaluate(...) on the dataset with three metrics—AnswerCorrectness, Faithfulness, and LLMContextRecall—passing in the wrapped LLM.

Stage 10 – Output
The evaluation object is turned into a pandas DataFrame, rounded to three decimal places, and printed with the heading “Evidence‐Aware Few‐Shot RAGAS Scores.”

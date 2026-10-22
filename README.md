# 📚 The Algorithms Study Assistant (RAG)

A Retrieval-Augmented Generation (RAG) application that allows users to ask questions about the book *Grokking Algorithms* and get precise answers with page citations.

## 🧠 How it Works
1. **Ingestion:** Extracts text from a 300-page PDF and chunks it by paragraph/line.
2. **Embedding:** Converts chunks into 3072-dimensional vectors using Google's `gemini-embedding-2`.
3. **Storage:** Stores vectors and page metadata in **ChromaDB**.
4. **Retrieval:** Finds the top 4 most relevant chunks for a user's question using semantic search.
5. **Generation:** Uses `gemini-3.6-flash` to generate an answer grounded *only* in the retrieved context.
6. **Guardrails:** 
   - **Distance Threshold:** Refuses to answer if the vector distance is too high (prevents hallucinations).
   - **Safety:** A regex scrubber blocks prompt injection attempts and scrubs PII (emails/phones).

## 🛠️ Stack
- **Language:** Python
- **LLM:** Google Gemini 3.6 Flash
- **Vector DB:** ChromaDB
- **Embeddings:** Gemini Embedding 2
- **Environment:** Google Colab

## 🚀 Example Query
**Q:** What is the difference between an array and a linked list?
**A:** Based on the provided context, the differences include:
* **Memory Storage:** In an array, all elements are stored right next to each other in memory, whereas in a linked list, elements are strewn all over memory [Page 27].
* **Access Type:** Arrays allow random access, meaning you can calculate positions instantly [Page 31]. Linked lists only allow sequential access [Page 31].
* **Strengths:** Arrays allow fast reads, while linked lists allow fast inserts and deletes [Page 39].

## 📈 Evaluation
The system was evaluated against a "Golden Set" of 10 core algorithm questions using a custom batch LLM-as-a-judge rubric. 
- **Initial Score:** 17/50 (Failed due to poor PDF chunking).
- **Optimized Score:** **46/50** (Achieved by implementing line-by-line chunking and relaxing the guardrail threshold).

# 📚 The Algorithms Study Assistant (RAG)

A Retrieval-Augmented Generation (RAG) application that allows users to ask questions about the book *Grokking Algorithms* and get precise answers with page citations.

## 🧠 How it Works
1. **Ingestion:** Extracts text from a 300-page PDF and splits it into paragraph-level chunks.
2. **Embedding:** Converts chunks into vectors using Google's `gemini-embedding-2`.
3. **Storage:** Stores vectors and page metadata in **ChromaDB**.
4. **Retrieval:** Finds the top 3 most relevant chunks for a user's question.
5. **Generation:** Uses `gemini-3.6-flash` to generate an answer grounded *only* in the retrieved context.
6. **Guardrails:** Includes a distance threshold (refuses to answer if the book doesn't cover it) and a PII/Prompt Injection scrubber.

## 🛠️ Stack
- **Language:** Python
- **LLM:** Google Gemini 3.6 Flash
- **Vector DB:** ChromaDB
- **Embeddings:** Gemini Embedding 2
- **Environment:** Google Colab

## 🚀 Example Query
**Q:** What is the difference between an array and a linked list?
**A:** Based on the provided context, the differences include:
* **Memory Storage:** Arrays store elements next to each other, while linked lists store elements anywhere, keeping track of addresses [Page 65].
* **Access Types:** Arrays provide random access (jumping directly to an element) [Page 53], while linked lists only allow sequential access [Page 57].
* **Performance:** Arrays are faster for reads, but linked lists allow fast inserts and deletes [Page 65].

## 📈 Evaluation
The system was tested against a "Golden Set" of 10 core algorithm questions using an LLM-as-a-judge rubric, scoring **X/50** on accuracy and faithfulness.
*(Replace X with your actual score from the evaluation run!)*

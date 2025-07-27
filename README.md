# UAT_Assignemt
**My Approach** -->
1. **Input Format**:
*I was provided with a logs.json file where each item had:< br / >
  *A system prompt (which acts like background/context).< br / >
  *A user prompt (the actual question).< br / >
  *An expected output (the LLM's answer).< br / >

2. **How I Evaluated**:
*I used a model called (all-MiniLM-L6-v2) from the sentence-transformers library.< br / >
*It converts text into embeddings and helps calculate semantic similarity using cosine similarity.< br / >
    *I compared:< br / >
      *System vs Answer --> to compute Faithfulness< br / >
      *User vs Answer --> to compute Answer_Relevancy< br / >
      *Context Chunks vs Answer --> to compute Context_Precision (I split the context into smaller parts and found the highest similarity)< br / >

3. **Why This Method?**
I don't have access to OpenAI’s paid API, so I used a local model to simulate similar behavior. This allowed me to test things like RAGAs-style scoring without relying on any online services.

--> **Libraries Used** <--
*"json" – for reading and parsing the input log file.< br / >
*"sentence-transformers" – to encode text as embeddings and compute similarities.< br / >
*"cosine similarity" - used via sentence-transformers.util.cos_sim() to measure how semantically similar two texts are.< br / >
*"torch" – used internally by sentence-transformers to run the embedding model.< br / >

--> **Assumptions and Simplifications** <--
1. I only used the first expected output from each log item.< br / >
2. If a system or user entry was missing, I handled it as an empty string to avoid errors.< br / >
3. I split long context into 300-character chunks to match how RAGAs evaluates context precision with partial matches.< br / >
4. I avoided any external API usage — everything runs completely offline.< br / >





**SETUP In Your Machine**:
Run this script offline using any IDE. Make sure you have latest version of python and all the dependecies install in your machine so you don't get any error.

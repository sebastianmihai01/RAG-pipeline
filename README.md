1. Requirements and observatiosn
Before I start, I need to gather a better understanding for the structure of the PDFs we work it because structure, semantics, rethorics or acronyms dictate how tokens fall into BoW, helps us understand what sanitization methods and how these get clustered together.The provided documents are formal RFP engineering documents with heavy taxonomy on regulation and compliance. The structure is clean, numbering is hierarchical, there are a lot of tables, bullet points and buzz-word abretivations.

Given that paragraphs are structured and follow a semantic, top-down approach, I choose a structure-aware chunking model as this context needs to be clearly reflected in the metadata we extract.
- Cleans and chunks: Chunks managed as mentioned above. Metadata of a chunk retains filename, title, page, section. For this reason, we use LangChain text splitter, given that paragraph are short and concise with clear section meaning, therefore each section can be a chunk with a few hundred tokens per request. If more chunks (or an entire page) would be sent to the LLM, there would be too much noise. The chunk size should be small enough to not cache noise noise but big enough to understand the semantic of the paragraph. Overlapping should be configured so each sentence is captured. 

- Embeds: the vector of word meanings can be small, we can use the text-embedding-3-small for the low cost

- Stores: for the vector DB, we can use Chroma since it syncs with Docker for local on-disk storage

- LLM: since the context is relatively short, we can use a model with no high reasoning thorughout psuch as 4o mini.

- Code/frameworks: we use pymupdf to parse the documents, FastAPI
--

- Tradeoff analysis:



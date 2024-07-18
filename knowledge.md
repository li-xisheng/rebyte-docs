## What is Knowledge?

> Handle unstructured data for your assistant.

Rebyte can auto sync your knowledge from various sources, such as Notion, Google Drive, GitHub, etc. For each knowledge, we chunk the document into many chunks, each chunk will be sent to LLM embedding service to get the embedding vector. 

In **Rebyte Tool**, you can use the knowledge action to do search over the knowledge base.

## How does Knowledge Work?

### Document

Each knowledge contains a list of documents, each document is identified by a unique document id within the knowledge.

### Chunk

The Document will be chunked into many chunks, each chunk identified by a unique chunk id within the document. Chunks will be sent to LLM embedding service to get the embedding vector.
When creating knowledge, user can specify the chunk size, which will determine how many chunks a document will have. Typically, chunk size ranges from a hundred to a few thousand tokens.

### Filter

Semantic search provides a way to search for similar content over the knowledge base. In additional to that, Filter provides a way to filter the search result by exact match. 

You can attach multiple tags to each document, for example, you can tag a document with "finance" and "report". When you do a search, you can filter the search result by "finance" and "report".

### Knowledge Data Connectors

* **File**: we support most of the file types, such as doc, docx, img, epub, jpeg, jpg, png, xls, xlsx, ppt, pptx, md, txt, rtf, rst, pdf, json, html.
* **Notion**: we support Notion API, you can sync your Notion pages to Rebyte.
* **Twitter**: we support Twitter API, you can sync specific Twitter accounts to Rebyte.
* **Web Page**: you can sync web pages to Rebyte.
* More connectors are coming.
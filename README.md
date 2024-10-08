# Web Data Analysis with LangChain and Streamlit

This project is a Streamlit-based web application that performs conversational data retrieval and question answering on web content. The application utilizes LangChain, OpenAI APIs, and Chroma for building a question-answering system that analyzes web data by fetching and vectorizing it into chunks.

## Features

- **Web Scraping**: The app allows users to input a website URL to extract text-based content.
- **Document Splitting**: Extracted content is split into manageable chunks for processing.
- **Vectorization**: The text chunks are vectorized using OpenAI embeddings, making it possible to search and retrieve relevant information based on user queries.
- **Conversational Context**: The app stores conversation history to create context-aware responses.
- **Real-Time Interaction**: Users can interact with the AI, ask questions about the extracted content, and get answers based on the context of the conversation.
  
## Requirements

To run the project, ensure the following Python packages are installed:

```bash
pip install streamlit langchain langchain-openai beautifulsoup4 python-dotenv chromadb
```

### API Requirements

You will need an OpenAI API key to run the application. Set your API key in the script by replacing `OPENAI_API_KEY` in the code with your actual key.

## How It Works

### Step-by-Step Process

1. **User Input for Website URL**:
   - The user provides a website URL via the sidebar input field. The application uses this URL to load and extract textual content from the page.
   
2. **Document Processing**:
   - The extracted content is divided into smaller chunks using `RecursiveCharacterTextSplitter` to manage large amounts of text effectively.
   
3. **Vectorization**:
   - The text chunks are transformed into vector embeddings using OpenAI embeddings with Chroma as the vector store.

4. **Question and Answer**:
   - Users can type questions in a conversational interface. The app retrieves the most relevant content from the website using LangChain's retriever models to provide accurate answers.
   
5. **Conversation Context**:
   - The app tracks the entire conversation, enabling history-aware interactions. This allows the AI to provide better answers based on previous inputs and responses.

### Files and Functions

- **`get_vectorstore_from_url(url)`**: Extracts text content from the specified URL and splits it into smaller chunks before vectorizing them.
- **`get_context_retriever_chain(vector_store)`**: Creates a retrieval chain that is aware of the conversation history.
- **`get_conversational_rag_chain(retriever_chain)`**: Combines the retriever chain with a conversation model to form the basis for question-answering.
- **`get_response(user_input)`**: Manages the process of fetching a response based on user input and the current conversation context.
  
### User Interface

The application has a simple, intuitive interface:
- **Main Page**: Displays the title and an input field for questions.
- **Sidebar**: Allows users to input a website URL for analysis.
- **Chat Interface**: Displays the conversation between the user and the AI, showing the user's queries and AI responses.

## Running the App

To run the app locally, use the following command:

```bash
streamlit run <script_name>.py
```

Where `<script_name>` is the name of the Python file containing the code.

## Example Use Case

1. The user enters a website URL (e.g., a blog post or news article) in the sidebar.
2. The user asks a question related to the content of the website.
3. The AI analyzes the text from the website and provides a response based on the retrieved information.

## Technologies Used

- **Streamlit**: For creating the user interface and handling real-time user input.
- **LangChain**: For building language model chains and managing the retrieval of relevant documents.
- **OpenAI**: For generating vector embeddings and answering questions using LLMs.
- **BeautifulSoup**: For web scraping and extracting the text from the provided website URL.
- **Chroma**: For storing and retrieving vectorized chunks of documents.

## Future Improvements

- **Error Handling**: Add error handling for cases when a website URL is invalid or inaccessible.
- **Extended Website Support**: Improve text extraction to handle more complex web pages.
- **Advanced Conversational Models**: Integrate more advanced conversational models for better user interactions.

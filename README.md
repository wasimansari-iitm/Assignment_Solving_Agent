## 🧠 AI Agent designed to autonomously solve the Graded Assignments

This project is an AI-powered file-processing and question-answering agent that accepts user-uploaded files (ZIP, CSV, PDF, Excel, JSON), analyzes them entirely in memory, and dynamically generates Python code using Mistral to solve structured data tasks — all securely executed in a sandboxed environment via FastAPI.

## 🚀 Features

- ✅ **AI-Generated Code Execution** using Mistral API (`mistral-small-latest`)
- 🔍 **File Type Identification** with format-specific logic
- 🧠 **Context-Aware Code Generation** based on file metadata + user question
- 💡 **In-Memory File Processing** (ZIP, CSV, JSON, Excel, PDF, etc.)
- 🔄 **Self-Debugging Workflow**: Automatic correction of errors via retry mechanism
- 🧾 **SHA256 Hashing**, Date normalization (ISO 8601), type conversions, etc.
- 🌐 **FastAPI Server** with CORS and deployable via Render or serverless platforms

## 📁 File Structure

- **blackbox.py**          # Core FastAPI app with Mistral integration & code execution logic
- **.env**                 # Contains MISTRAL_API_KEY (Expires on 30th April, 2025)
- **requirements.txt**     # All required packages for deployment


## 🛠 Technologies Used

- **FastAPI** – REST API framework
- **Mistral API** – For generating Python code
- **Mangum** – AWS Lambda support (optional)
- **Pandas, pdfplumber, openpyxl, numpy, PIL** – For structured file parsing
- **Docker** – Deployment-ready containerization
- **Render** – One-click deployment compatible

## 📦 API Endpoint

### `POST /submit`

| Parameter     | Type          | Required | Description                              |
|---------------|---------------|----------|------------------------------------------|
| `question`    | `string`      | ✅       | Natural language question or task        |
| `file`        | `UploadFile`  | ❌       | Optional uploaded file for analysis      |

### Example Curl:
```bash
curl -X POST http://localhost:8000/submit \
  -F 'question=Extract all names and compute their frequency' \
  -F 'file=@data.zip'
```

## 🧪 Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Set your Mistral API key in a .env file
echo "MISTRAL_API_KEY=your_api_key_here" > .env

# Run the server
python blackbox.py
```

## 🐳 Deployment on Render

Render fetches the GitHub repo and builds a Docker image automatically.

- Rebuilds the app image automatically everytime if change is commited in the repository.
- Ensures smooth and streamlined deployment until April 30th, 2025.

## 🤖 System Prompt

The agent is prompted with a comprehensive instruction set to:
- Validate and parse files
- Generate safe Python code
- Handle errors robustly
- Return clean, structured results

## 📜 License

MIT

## 🙋‍♂️ Author

Wasim Ansari – Built as part of a Data Science Diploma project from IIT Madras.

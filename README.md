# Arabic Documents QA Chatbot - Linux Setup Guide

## Overview
This application is a Streamlit-based chatbot that allows users to upload Arabic documents (PDF, DOCX, TXT) and ask questions about their content using OpenAI's GPT models. It features user authentication, admin controls, and vector-based document search.

## System Requirements
- Linux distribution (Ubuntu 20.04+ recommended)
- Python 3.8 or higher
- At least 2GB RAM
- 1GB free disk space
- Internet connection for OpenAI API calls

## Step 1: Install Python and System Dependencies

### For Ubuntu/Debian:
```bash
# Update package list
sudo apt update

# Install Python 3 and pip
sudo apt install python3 python3-pip python3-venv

# Install system dependencies for PDF processing
sudo apt install python3-dev build-essential

# Verify Python installation
python3 --version
pip3 --version
```
## Step 2: Create Project Directory and Virtual Environment

```bash
# Create project directory
mkdir arabic-qa-chatbot
cd arabic-qa-chatbot

# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate

# Upgrade pip
pip install --upgrade pip
```

## Step 3: Install Required Packages

Create a `requirements.txt` file with the following content:

```txt
streamlit==1.29.0
openai==1.3.0
langchain==0.0.350
langchain-openai==0.0.2
faiss-cpu==1.7.4
PyPDF2==3.0.1
python-docx==1.1.0
arabic-reshaper==3.0.0
python-bidi==0.4.2
pathlib==1.0.1
```

Install the requirements:
```bash
pip install -r requirements.txt
```

## Step 4: Download and Setup the Application

1. Save the main application code as `app.py` in your project directory
2. Create the necessary directory structure:

```bash
mkdir -p data/files data/users data/vectorstore
```

## Step 5: Configure OpenAI API Key

**Important Security Note:** The current code has a placeholder API key. You must replace it with your actual OpenAI API key.

### Method 1: Modify the code (Less Secure)
Edit `app.py` and replace:
```python
OPENAI_API_KEY = "x"
```
with:
```python
OPENAI_API_KEY = "your-actual-openai-api-key-here"
```

## Step 6: Run the Application

```bash
# Make sure virtual environment is activated
source venv/bin/activate

# Run the Streamlit app
streamlit run app.py
```

The application will be available at `http://localhost:8501`

## Step 7: Initial Login

- **Default Admin Credentials:**
  - Username: `admin`
  - Password: `admin123`

**Important:** Change the default admin password immediately after first login for security.

## Directory Structure

After setup, your project should look like this:
```
arabic-qa-chatbot/
├── venv/                    # Virtual environment
├── data/
│   ├── files/              # Uploaded documents
│   ├── users/              # User database
│   └── vectorstore/        # FAISS vector database
├── app.py                  # Main application
├── requirements.txt        # Python dependencies              
└── README.md              # This documentation
```

## Usage Instructions

### For Administrators:
1. Log in with admin credentials
2. Upload documents in the "رفع المستندات" (Upload Documents) tab
3. Manage users in the "إدارة المستخدمين" (User Management) tab
4. Test the system in the "اختبار النظام" (System Test) tab

### For Regular Users:
1. Log in with user credentials
2. Ask questions about uploaded documents in Arabic
3. The system will provide answers based on the document content


## Troubleshooting

### Common Issues:

1. **Import Errors:**
   - Ensure virtual environment is activated
   - Reinstall requirements: `pip install -r requirements.txt`

2. **FAISS Installation Issues:**
   - Install system dependencies: `sudo apt install build-essential`
   - Use CPU version: `pip install faiss-cpu`

3. **Arabic Text Display Issues:**
   - Ensure proper font support: `sudo apt install fonts-noto`

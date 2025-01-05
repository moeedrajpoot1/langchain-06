# Image and Video Analysis using LangChain and Gemini AI

This repository demonstrates how to use LangChain with Google's Gemini AI for analyzing images and videos. The workflow integrates LangChain's prompt engineering with Gemini AI's generative capabilities to process multimedia content.

---

## Prerequisites

1. Python 3.8+
2. Install the required libraries:
   ```bash
   pip install langchain-google-genai
   pip install google-generativeai
   ```
3. A Google Gemini AI API key.

---

## Features

- Analyze images and generate descriptive responses.
- Process video files and describe their content.

---

## Setup

### Install Dependencies
Ensure you have the necessary Python libraries installed:
```bash
pip install langchain-google-genai google-generativeai
```

### Configure API Key
Replace the placeholder API key with your valid Google Gemini AI API key:
```python
api_key = "YOUR_API_KEY_HERE"
```

---

## Code Examples

### Image Analysis
The following code analyzes an image using LangChain and Gemini AI:
```python
import langchain_google_genai as genAI
from langchain.prompts import PromptTemplate
from langchain.chains import LLMChain
from langchain_google_genai import ChatGoogleGenerativeAI
from langchain_core.messages import HumanMessage

llm = ChatGoogleGenerativeAI(
    api_key="YOUR_API_KEY_HERE",
    model="gemini-2.0-flash-exp",
    temperature=1.0  # Adjust for creativity
)

message = HumanMessage(
    content=[
        {
            "type": "text",
            "text": "What's in this image?",
        },
        {"type": "image_url", "image_url": "https://picsum.photos/seed/picsum/200/300"},
    ]
)
response = llm.invoke([message])
print(response)
```

### Video Analysis
The following code analyzes a video file:
```python
import google.generativeai as genai

# Configure the model
genai.configure(api_key="YOUR_API_KEY_HERE")
model = genai.GenerativeModel('gemini-2.0-flash-exp')

# Process the video
video_path = "path_to_your_video.mp4"
with open(video_path, "rb") as video_file:
    video_data = video_file.read()

# Create content with correct structure
content = [
    "What's happening in this video?",
    {
        "mime_type": "video/mp4",
        "data": video_data
    }
]

# Generate response
response = model.generate_content(content)
print(response.text)
```

---

## Notes

- Ensure the image or video file is accessible and correctly formatted.
- Adjust the model's temperature parameter to control creativity and variability in responses.

---

## License
This project is licensed under the MIT License.

---

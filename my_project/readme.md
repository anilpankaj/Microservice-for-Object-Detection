# Microservice for Object Detection

This project comprises two main components:

1. **UI Backend Service**: Accepts image input from the user.
2. **AI Backend Service**: Uses YOLOv8 for object detection and returns results in a structured JSON format.



## Prerequisites

Ensure you have the following installed on your system:

- **Docker**
- **Python**


## Setup

Follow these steps to set up the project:

1. Clone the repository:
   
   git clone <repository_url>
   
2. Navigate to the project directory:
   
   cd my_project
   

## Project Structure

The project is organized as follows:

my_project/
├── ai_backend/
│   ├── Dockerfile
│   ├── main.py
│   ├── requirements.txt
├── ui_backend/
│   ├── Dockerfile
│   ├── main.py
│   ├── requirements.txt
├── docker-compose.yml
└── README.md


## Running the Services

### Build and Run Services

Use Docker Compose to build and run the services:

1. Open the terminal and navigate to the `my_project` directory:
   
   cd my_project

2. Run the following command to build and start the services:
   
   docker-compose up --build
   


## Testing the Endpoint

### Step 1: Start the AI Backend Server

1. Open a new terminal and navigate to the `my_project/ai_backend` directory:
   
   cd my_project/ai_backend
   
2. Start the FastAPI application:
   
   uvicorn main:app --reload
   

### Step 2: Upload an Image to the UI Backend

1. Open the `git bash terminal` and run the following command (replace the file path with the path to your test image):
   
   curl -X POST "http://127.0.0.1:8000/detect" \
        -H "accept: application/json" \
        -H "Content-Type: multipart/form-data" \
        -F "file=@<path_to_your_image>"
   
   Example:

   curl -X POST "http://127.0.0.1:8000/detect" \
        -H "accept: application/json" \
        -H "Content-Type: multipart/form-data" \
        -F "file=@E:/Kobe2.0/my_project/test.jpg"

The server will process the image and return the object detection results in JSON format and saved the detection image locally in my_project/ai_backend directory.
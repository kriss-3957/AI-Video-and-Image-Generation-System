

# AI Video and Image Generation System

## Overview
This project is an AI-based system that generates motivational videos and images from user-provided text prompts. It uses state-of-the-art AI tools like Stable Diffusion and other text-to-video generation pipelines to create content. The project includes user authentication, content storage, and a web interface for viewing and managing the generated content.

## Features
- Accepts text prompts to generate images and videos.
- Generates:
  - 5 motivational videos in `.mp4` format.
  - 5 motivational images in `.png` format.
- Stores content in user-specific directories.
- Provides a user-friendly web interface built with Flask.
- Tracks generation progress and notifies users upon completion.
- Includes a database for managing user data, prompts, and generation statuses.

---


---


## Technical Details

### 1. Image and Video Generation
- **Images**: Generated using `StableDiffusionXLPipeline`.
- **Videos**: Generated using `Damo-vilab/text-to-video-ms-1.7b`.

### 2. Database
- SQLite is used to store:
  - `user_id`: Unique identifier for each user.
  - `prompt`: User-provided text prompt.
  - `video_paths`: Paths to generated videos.
  - `image_paths`: Paths to generated images.
  - `status`: Status of content generation (`Processing` or `Completed`).
  - `generated_at`: Timestamp of content generation.

### 3. Web Interface
- Built using Flask.
- Templates include:
  - **`login.html`**: Simple login page.
  - **`home.html`**: Main page to input prompts and view generated content.

### 4. File Structure

## Project File Structure

```
project/
│   └── templates/
│       ├── login.html
│       └── home.html
│
├── models.py
├── app.py
├── requirements.txt
├── generated_content
├── app.db
└── db.py
```



---
---

## Code Walkthrough

---
---
### `models.py`
Contains the core functions for generating images and videos using AI pipelines:
- **`generate_image(prompt, user_id)`**: Generates and saves images.
- **`generate_video(prompt, user_id, num_videos)`**: Generates and saves videos.

### `app.py`
The main Flask application for user interaction and content display:
- User login and session management.
- Routing for content generation and display.
- Ngrok setup for public access.

### `db.py`
Handles database initialization and CRUD operations:
- **`init_db()`**: Creates the database schema.
- **`save_user_data()`**: Saves or updates user data.
- **`get_user_data(user_id)`**: Retrieves user data.

### HTML Templates
- **`login.html`**: Provides a user-friendly login page.
- **`home.html`**: Displays the prompt input form, status messages, and generated content.

---

## Dependencies

All required Python libraries are listed in `requirements.txt`:
diffusers==0.23.0 
transformers>=4.44.0 
peft>=0.4.0 
accelerate>=0.21.0 
flask 
torch 
torchvision 
pyngrok 
safetensors 
imageio[ffmpeg] 
plyer 
huggingface_hub==0.25.0


---
---

# Setup & Usage Instructions
---
---
## Prerequisites
- **Python**: Ensure Python 3.8 or higher is installed.
- **CUDA**: For GPU-based acceleration, ensure CUDA is installed and configured.
- **Dependencies**: Install required Python libraries from `requirements.txt`.

---

## Installation

1. Download the project.zip file from the repository:
```
!wget -O project.zip https://github.com/kriss-3957/AI-Video-and-Image-Generation-System/blob/main/project.zip
```


### 2. Unzip the downloaded file:

```
!unzip project -d /content/project
```


## 3. Set the directory to the project folder
```
!cd /content/project
```




## 4. Set the ngrok Authentication Token:

This project uses ngrok to expose our local Flask application to the internet, making it accessible through a public URL. To use ngrok, you need to set up an authentication token. Follow these steps:
```
Step 1: Obtain Your ngrok Authentication Token
1. Sign up for a free ngrok account at [ngrok.com](https://ngrok.com/).
2. Log in to your ngrok dashboard.
3. Locate your authentication token on the "Get Started" page or under the "Auth" section of your account.

Step 2: Add the Token to the Project
Edit the 'authtoken.env' environmen t variable file in the project repository and replace <your_ngrok_auth_token_here> with your actual Authtoken and save it.

```

## 5. Install dependencies:
```
!pip install -r requirements.txt
```

## 6. Run the Flask app to generate and serve content:
```
!python app.py
```


## 7. Access the Web Interface:

Visit or share the Ngrok public URL (displayed in the console) or `http://localhost:5000` for local access.


## 8. Navigating the app:
```
Step 1: Log in and Generate Content
- Log in with a unique `User ID`.
- Enter a prompt to generate images and videos.

Step 2: View Generated Content
- Generated content will appear in a gallery once ready.
- If still processing, a notification will be displayed.

Step 3:Notifications generated

- The system notifies users via the console when content generation is complete.
- Notifications include a link to the web page where users can view their content.

```
---

## Example Workflow

1. **User Login**: Enter a `User ID` to log in.
2. **Enter Prompt**: Provide a motivational text prompt (e.g., "The sunrise inspires hope").
3. **Generation**: The system generates:
   - 5 videos stored as `video_1.mp4`, `video_2.mp4`, ..., `video_5.mp4`.
   - 5 images stored as `image_1.png`, `image_2.png`, ..., `image_5.png`.
4. **View Content**: Access generated content on the home page.

We could also directly run the |
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/kriss-3957/AI-Video-and-Image-Generation-System/blob/main/quickstart_colab.ipynb) | quickstart_colab.ipynb | notebook in colab with a GPU runtime, to launch the flask app.

---


## Video Walkthrough

[**Click here**](<Insert-Your-Video-Link>) to watch a video explaining the setup and functionality of the system.

---

## Future Enhancements
- Add user email notifications for completed content.
- Enable content deletion or regeneration options.
- Increase the durations of the generated video using more gpu compute.
- Enhance UI for a better user experience.
- Add support for multiple concurrent users with better queue management.


---

## Contact
For questions or feedback, please contact:
- **Email**: kriss.dbpc@gmail.com
- **LinkedIn**: [----](https://t.me/YourHandle)















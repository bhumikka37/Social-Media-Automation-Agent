# AI Video + Sound Automation with n8n

## 📌 Project Overview
This project demonstrates how to automate **video and audio generation workflows** using **n8n**, an open-source workflow automation tool.  
The workflow integrates with external AI APIs (PiAPI in this case) to:

1. Take **text prompts** as input.
2. Generate **images or videos** using AI models (txt2img or img2video).
3. Poll the API until the video is ready (status changes from `pending` to `succeeded`).
4. Fetch and return the **video URL** and **sound file URL**.
5. Output a structured JSON with scene titles, video URLs, and sound URLs.

---

## ⚙️ Key Concepts

### 🔹 n8n
n8n is a **workflow automation platform** that connects apps and APIs with a drag-and-drop interface.  
It allows you to automate tasks without needing to code everything from scratch.

### 🔹 Polling
APIs often return a `pending` status when a task (like generating a video) takes time.  
To handle this, we use **polling**:
- Wait a few seconds
- Check the status again
- Repeat until status = `succeeded`

### 🔹 Workflow Flow
1. **Trigger**: User submits a form with a content idea (text prompt).
2. **AI API Call**: Send the text prompt to PiAPI (txt2img / img2video model).
3. **Wait + Check Loop**:  
   - If status = `pending`, wait 5–10 seconds and check again.  
   - If status = `succeeded`, move forward.
4. **Collect Data**: Store the video URL and audio file link.
5. **Final Output**: JSON with scene title, video URL, and sound URL.

---

## 🛠️ Example Output

```json
[
  {
    "scene_titles": ["mammals traveling through the jungle"],
    "video_urls": ["https://example.com/generated-video.mp4"],
    "sounds_urls": ["https://drive.google.com/uc?id=1HJNv3FySwtcs_ntj9792EnPeKN138Geu&export=download"]
  }
]
```

---

## 🚀 Benefits of This Project
- Automates manual API calls into a single seamless workflow.
- Handles **long-running tasks** with polling inside n8n.
- Produces **structured outputs** ready for further use (apps, dashboards, websites).
- Saves time by reducing repetitive tasks.

---

## 📂 Files
- **README.md** → This file (project explanation).
- **n8n workflow file** (optional) → Can be exported from n8n for reuse.

---

## 📖 How to Use
1. Install **n8n** locally (`npm install n8n -g`) or use the cloud version.
2. Import the workflow file (if exported).
3. Set up credentials for **PiAPI** and **Google Drive (or storage API)**.
4. Run the workflow and test with a text prompt.

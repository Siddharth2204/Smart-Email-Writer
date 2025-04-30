
# ✉️ AI Email Reply Generator - Chrome Extension

This is a Chrome Extension powered by a Spring Boot backend and the **Gemini AI API**, designed to generate professional email replies in Gmail with a single click. It uses natural language processing to understand the email content and provide context-aware responses instantly.

---

## 📌 Features

- 🧠 Uses Gemini (Google's LLM) API for generating intelligent replies
- 📬 Works directly within Gmail interface
- 🚀 Spring Boot backend handles API requests and AI integration
- 🌐 Fetches email content using DOM selectors
- 🔒 CORS enabled backend
- 🧪 Tested via Postman before front-end integration

---

## 🧰 Tech Stack

| Layer       | Technology                         |
|-------------|-------------------------------------|
| Frontend    | JavaScript, HTML, CSS, Chrome APIs |
| Backend     | Java (Spring Boot), Maven          |
| API         | Gemini Pro (Google Generative AI)  |
| Testing     | Postman                            |

---

## 📂 Project Structure

```
ai-email-reply-extension/
│
├── backend/                 # Spring Boot Backend
│   ├── src/
│   │   └── main/java/com/email/...
│   └── application.properties
│
├── extension/               # Chrome Extension
│   ├── manifest.json
│   ├── content.js
│   ├── background.js
│   └── popup.html
│
├── postman/                 # Postman collection (optional)
│   └── email-api.postman_collection.json
│
└── README.md
```

---

## 🚀 How It Works

1. **User opens Gmail.**
2. The Chrome Extension injects an "AI Reply" button into the email compose/reply toolbar.
3. On clicking the button:
   - JavaScript extracts the email content from the DOM.
   - A POST request is made to the Spring Boot backend with the email text and tone.
   - The backend formats this input and sends it to **Gemini Pro API**.
   - Gemini generates a professional reply based on the given context.
   - The reply is sent back and inserted into Gmail's compose box.

---

## 🧪 Using Postman (Before Frontend Integration)

To test backend independently:

1. **Start the Spring Boot app** (`localhost:8080`)
2. Open Postman and create a POST request to:

```
POST http://localhost:8080/api/email/generate
```

**Body (raw JSON):**
```json
{
  "emailContent": "Hi, I would like to schedule a meeting next week.",
  "tone": "professional"
}
```

You should receive a generated response like:
```text
Thank you for your email. I would be happy to schedule a meeting next week. Please let me know your available dates and times.
```

---

## ⚙️ Configuration

**application.properties (Spring Boot)**:
```properties
spring.cors.allowed-origins=http://localhost:3000,chrome-extension://*
gemini.api.key=YOUR_API_KEY
```

Make sure you replace `YOUR_API_KEY` with your actual Gemini Pro key.

---

## 🧠 Gemini API Integration

- Uses `@Value` to inject Gemini API key from properties
- Makes POST request to Google’s `https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent`
- Parses the JSON and returns the generated reply

---

## 🛡️ Permissions (Chrome Extension)

`manifest.json` includes:
```json
"permissions": [
  "activeTab",
  "scripting"
],
"host_permissions": [
  "https://mail.google.com/"
]
```

---

## 📥 Installation (for Chrome)

1. Go to `chrome://extensions/`
2. Enable **Developer Mode**
3. Click on **Load Unpacked**
4. Select the `extension/` folder

---

## 🧑‍💻 Author

Made with ❤️ for smarter and faster email communication.

> Category of Project: **AIML**  
> Frontend: **Chrome Extension (HTML, JS, CSS)**  
> Backend: **Spring Boot (Java)**  
> AI API: **Gemini Pro (Google GenAI)**  
> Tools Used: **Postman, IntelliJ, Chrome DevTools**

---

## 📄 License

This project is licensed under the MIT License. Feel free to use, modify, and distribute it.

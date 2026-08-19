# Prompt2ServiceNow

**Prompt2ServiceNow** is an AI-powered tool that helps ServiceNow developers generate scripts and configurations using simple, natural-language prompts — cutting down manual coding time and speeding up development.

Instead of writing ServiceNow scripts line by line, describe what you need in plain English, and Prompt2ServiceNow generates the corresponding artifact (Business Rule, Client Script, UI Policy, Script Include, etc.) ready to use in your instance.

---

## ✨ Features

- 🗣️ **Natural Language to ServiceNow Code** — Describe a requirement in plain English and get working ServiceNow script logic in return.
- ⚙️ **Multi-Artifact Support** — Generates:
  - Business Rules
  - Client Scripts
  - UI Policies
  - Script Includes
  - Other common ServiceNow components
- 🔌 **Scripted REST API Integration** — Uses a custom Scripted REST API on the ServiceNow instance to receive generated JSON and create/update the corresponding artifact directly.
- 🤖 **AI-Powered Generation** — Uses the Gemini API to interpret prompts and produce structured, ServiceNow-compatible output.
- 🌐 **Simple Web Interface** — A lightweight HTML front end to enter prompts and trigger generation.

---

## 🏗️ How It Works

1. The user enters a natural-language prompt describing the desired ServiceNow logic (e.g., *"Create a Business Rule that sets priority to High when impact and urgency are both High"*).
2. The prompt is sent to the **Gemini API**, which interprets the request and generates the corresponding ServiceNow artifact as structured JSON.
3. The generated JSON is pushed to the ServiceNow instance via a **Scripted REST API**, which creates or updates the relevant record (Business Rule, Client Script, etc.).
4. The developer reviews and refines the generated artifact directly inside ServiceNow.

---

## 📂 Project Structure

| File | Description |
|------|-------------|
| `servicenow.html` | Front-end interface for entering prompts and interacting with the tool |
| `ScriptedRest.text` | Scripted REST API script (ServiceNow side) that receives generated JSON and creates the artifact |
| `HOME PAGE.png` | Screenshot/preview of the tool's home page |

---

## 🚀 Getting Started

### Prerequisites
- A ServiceNow developer instance
- A Gemini API key
- Basic familiarity with ServiceNow Scripted REST APIs

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/Vikash8294/Prompt2ServiceNow.git
   ```
2. Import the `ScriptedRest.text` script into a **Scripted REST API** resource on your ServiceNow instance.
3. **Create a CORS Rule** on your ServiceNow instance so the front end can call the Scripted REST API (see [CORS Rule](#-cors-rule-setup) below).
4. Open `servicenow.html` in a browser (or host it) and configure it to point to:
   - Your Gemini API endpoint/key
   - Your ServiceNow instance's Scripted REST API URL
5. Enter a prompt describing the ServiceNow artifact you want, and submit.
6. Check your ServiceNow instance for the newly created/updated artifact.

---

## 🌍 CORS Rule Setup

Since `servicenow.html` calls the ServiceNow Scripted REST API directly from the browser (a different origin), a **CORS Rule** must be created on the ServiceNow instance — otherwise the request will be blocked by the browser.

**Steps to create the CORS Rule:**

1. In your ServiceNow instance, navigate to **System Web Services > REST > CORS Rules**.
2. Click **New**.
3. Fill in the fields:
   - **Name**: `Prompt2ServiceNow CORS Rule`
   - **REST API**: Select the Scripted REST API created from `ScriptedRest.text` (or leave as `*` to apply globally)
   - **Domain**: The origin where `servicenow.html` is hosted (e.g., `http://localhost:5500`, `https://yourdomain.com`, or `*` for testing only)
   - **HTTP Methods**: `GET`, `POST` (add others if needed)
4. Under **HTTP headers**, add the headers your front end sends (typically `Content-Type`, `Authorization`).
5. Save the record.
6. Test the request from `servicenow.html` — it should no longer be blocked by CORS.

> ⚠️ Avoid using `*` for the domain in production. Restrict it to the exact origin hosting your front end.

---

## 🖼️ Preview

### Home Page
<img width="1919" height="873" alt="Home Page Screenshot" src="https://github.com/user-attachments/assets/42c9719a-1011-401e-a45a-2a5755940b90" />

### CORS Rule
<img width="1917" height="882" alt="CORS Rule Screenshot" src="https://github.com/user-attachments/assets/248f685c-17fc-4477-8080-13b8d0f22487" />

### Demo Video

https://github.com/user-attachments/assets/ae57ecab-3fee-4038-931d-fa4d0051f249



*Click the thumbnail above to watch the full demo video*

---

## 🛣️ Roadmap

- [ ] Add support for more artifact types (UI Actions, ACLs, Notifications)
- [ ] Add validation/preview before pushing changes to ServiceNow
- [ ] Improve prompt parsing for complex, multi-condition logic
- [ ] Add authentication for secure API usage

---

## 🤝 Contributing

Contributions, suggestions, and feature requests are welcome! Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is currently unlicensed. Add a license file if you'd like to specify usage terms.

---

## 👤 Author

**Vikash**
[GitHub Profile](https://github.com/Vikash8294)

---

## 📬 Contact

For questions or suggestions, feel free to open an issue or contact [Vikash8294](https://github.com/Vikash8294).

---

*Simplifying ServiceNow development, one prompt at a time!*


# # How to Use Claude Code with Qwen Models for Free

*(Windows CMD Version — Customized by Rimza)*

This guide explains how to use **Claude Code** with **Qwen models for free** using the Claude Code Router.
Everything is tailored specifically for your system:

---

# ⭐ Requirements

Before you start, make sure the following are installed:

### **1. Qwen CLI**

Installed and authenticated.

### **2. Node.js v18 or later**

Check with:

```
node -v
```

---

# 🧩 Qwen CLI Installation

Install the Qwen Code CLI:

```
npm install -g @qwen-code/qwen-code@latest
```

Verify the installation:

```
qwen --version
```

---

# 🚀 Step 1: Install Claude Code Router

Install Claude Code and the router globally:

```
npm install -g @anthropic-ai/claude-code @musistudio/claude-code-router
```

---

# 🔑 Step 2: Get Your Qwen Access Token

Your Qwen authentication file is stored here:

```
C:\Users\HP\.qwen\oauth_creds.json
```

Open it and you will see:

```json
{
  "access_token": "YOUR_QWEN_ACCESS_TOKEN_HERE",
  "token_type": "Bearer",
  "refresh_token": "YOUR_QWEN_REFRESH_TOKEN_HERE",
  "resource_url": "portal.qwen.ai",
  "expiry_date": 1764876220290
}
```

Copy your **access_token** — you will add it to the router config.

---

# 📁 Step 3: Create Required Folders

Open CMD and run:

```
mkdir C:\Users\HP\.claude-code-router
mkdir C:\Users\HP\.claude
```

---

# ⚙️ Step 4: Create the Router Configuration

Open the config file in **Notepad**:

```
notepad C:\Users\HP\.claude-code-router\config.json
```

Paste the following into the file:

```json
{
  "LOG": true,
  "LOG_LEVEL": "info",
  "HOST": "127.0.0.1",
  "PORT": 3456,
  "API_TIMEOUT_MS": 600000,
  "Providers": [
    {
      "name": "qwen",
      "api_base_url": "https://portal.qwen.ai/v1/chat/completions",
      "api_key": "YOUR_QWEN_ACCESS_TOKEN_HERE",
      "models": [
        "qwen3-coder-plus",
        "qwen3-coder-plus",
        "qwen3-coder-plus"
      ]
    }
  ],
  "Router": {
    "default": "qwen,qwen3-coder-plus",
    "background": "qwen,qwen3-coder-plus",
    "think": "qwen,qwen3-coder-plus",
    "longContext": "qwen,qwen3-coder-plus",
    "longContextThreshold": 60000,
    "webSearch": "qwen,qwen3-coder-plus"
  }
}
```

Replace:

```
YOUR_QWEN_ACCESS_TOKEN_HERE
```

with your actual Qwen access token.

Save → Close Notepad.

---

# ▶️ Step 5: Start Using Claude Code with Qwen

Start the router:

```
ccr start
```

Then open Claude Code:

```
ccr code
```

Test:

```
> hi
```

If it replies → setup is working correctly.

---

# 🔄 Handling 401 Token Errors (Expired Token)

If you see:

```
401 Unauthorized
```

Your Qwen token expired.
Follow these steps:

---

### **1️⃣ Reauthenticate**

Run:

```
qwen
```

This refreshes your token.

---

### **2️⃣ Update Your Router Config**

Open the config again in CMD/Terminal:

```
notepad C:\Users\HP\.claude-code-router\config.json
```

Replace the old token with the **new access_token**.

Save → Close.

---

### **3️⃣ Restart the Router**

Run:

```
ccr restart
```
### **3️⃣ Start**
Run:

```
ccr start
```
### **3️⃣ Open another terminal and write**
Run:

```
ccr code 
```


Everything should now work again.

---

# ✅ Done!

by Rimza


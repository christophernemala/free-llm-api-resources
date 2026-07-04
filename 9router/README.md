# 9Router Setup Guide

This guide is for the GitHub repository:

```text
https://github.com/decolua/9router
```

9Router is a local AI router. It gives your coding tools one OpenAI-compatible endpoint and then routes requests to supported providers/models.

```text
Your coding tool
      ↓
9Router local server
      ↓
Connected provider/model
```

Official local endpoint:

```text
http://localhost:20128/v1
```

Official dashboard:

```text
http://localhost:20128/dashboard
```

---

## 1. Requirements

Install these first:

```text
Node.js LTS
npm
Git
```

Check installation:

```bash
node -v
npm -v
git --version
```

---

## 2. Easy install from npm

Use this when you only want to run 9Router.

```bash
npm install -g 9router
9router
```

Then open:

```text
http://localhost:20128/dashboard
```

---

## 3. Run from GitHub source

Use this when you want the actual repository code locally.

```bash
git clone https://github.com/decolua/9router.git
cd 9router
cp .env.example .env
npm install
PORT=20128 NEXT_PUBLIC_BASE_URL=http://localhost:20128 npm run dev
```

Then open:

```text
http://localhost:20128/dashboard
```

---

## 4. Production run from source

```bash
npm run build
PORT=20128 HOSTNAME=0.0.0.0 NEXT_PUBLIC_BASE_URL=http://localhost:20128 npm run start
```

For learning, prefer localhost first.

---

## 5. Connect provider in dashboard

Open:

```text
http://localhost:20128/dashboard
```

Then follow:

```text
Dashboard → Providers → Connect Provider
```

Start with a supported free provider shown inside the dashboard, or connect an API-key provider if you already have a key.

---

## 6. Configure a coding tool

Use OpenAI-compatible settings.

```text
Base URL / Endpoint:
http://localhost:20128/v1

API Key:
Copy from 9Router dashboard

Model:
Copy selected model name from 9Router dashboard
```

Example layout:

```text
Provider: OpenAI Compatible
Base URL: http://localhost:20128/v1
API Key: <9router-dashboard-key>
Model: <selected-9router-model>
```

---

## 7. Test

Ask your coding tool:

```text
Create a simple hello world JavaScript file.
```

If the tool responds, your setup is working.

---

## 8. Common errors

### Error: command not found: 9router

Fix:

```bash
npm install -g 9router
```

Then restart terminal.

### Error: localhost not opening

Check whether 9Router is running:

```bash
9router
```

Then open:

```text
http://localhost:20128/dashboard
```

### Error: provider not working

Check:

```text
1. Provider is connected in dashboard
2. API key is correct
3. Model name is copied exactly
4. Base URL is http://localhost:20128/v1
```

---

## 9. Security note

Keep 9Router local while learning.

Recommended:

```text
localhost only
```

Avoid public exposure until you understand authentication, firewall rules, and reverse proxy security.

---

## 10. Simple mental model

```text
9Router is not the AI model.
9Router is the traffic controller.
Your coding tool sends requests to 9Router.
9Router sends the request to the selected model/provider.
9Router returns the answer back to your coding tool.
```

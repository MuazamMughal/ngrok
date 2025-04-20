# Ngrok Complete Learning Guide

Welcome to the **Ngrok Learning Guide**. This `README.md` file will help you understand what Ngrok is, how it works, and how to use it effectively in your development workflow.

---

## 📌 Table of Contents
- [What is Ngrok?](#what-is-ngrok)
- [Why Use Ngrok?](#why-use-ngrok)
- [How Ngrok Works](#how-ngrok-works)
- [Installing Ngrok](#installing-ngrok)
- [Creating a Tunnel](#creating-a-tunnel)
- [Use Cases](#use-cases)
- [Ngrok Dashboard](#ngrok-dashboard)
- [Custom Domains & Auth](#custom-domains--auth)
- [Using Ngrok with Webhooks](#using-ngrok-with-webhooks)
- [Advanced Features](#advanced-features)
- [Security Best Practices](#security-best-practices)
- [Troubleshooting](#troubleshooting)
- [References](#references)

---

## 🤔 What is Ngrok?

**Ngrok** is a tool that allows you to expose a local server to the internet using secure tunnels. It provides a public URL that tunnels HTTP or TCP traffic to your local machine.

---

## 🚀 Why Use Ngrok?

- Share local apps with teammates or clients
- Test APIs or apps on real mobile devices
- Receive webhooks from services like Stripe, GitHub, etc.
- Demo projects instantly
- Inspect traffic for debugging purposes

---

## 🧠 How Ngrok Works

1. You start a local server (e.g., `localhost:3000`).
2. Run `ngrok http 3000`.
3. Ngrok generates a public URL like `https://abcd1234.ngrok.io`.
4. This URL tunnels requests to your local server.

---

## 🛠️ Installing Ngrok

### Step 1: Download Ngrok
Go to [https://ngrok.com/download](https://ngrok.com/download) and download the version for your OS.

### Step 2: Unzip & Install
```bash
unzip ngrok-stable-linux-amd64.zip
mv ngrok /usr/local/bin
```

### Step 3: Authenticate Ngrok
Sign up at [https://dashboard.ngrok.com](https://dashboard.ngrok.com), then run:
```bash
ngrok config add-authtoken <your_auth_token>
```

---

## 🔄 Creating a Tunnel

### HTTP Tunnel
```bash
ngrok http 3000
```
This exposes your local server on port 3000.

### TCP Tunnel
```bash
ngrok tcp 22
```
This exposes SSH on port 22.

---

## 💡 Use Cases

- **Webhooks:** Receive webhook data on local dev
- **Mobile Testing:** Test your local site on mobile devices
- **Client Demos:** Instantly demo work
- **IoT Devices:** Connect remote devices to your dev server

---

## 📊 Ngrok Dashboard

Ngrok provides a web interface at `http://127.0.0.1:4040` to inspect requests:

- Request logs
- Headers
- Payloads
- Replay requests

---

## 🌐 Custom Domains & Auth

### Custom Subdomain
```bash
ngrok http -subdomain=myapp 3000
```

### Basic Authentication
```bash
ngrok http -auth="user:password" 3000
```

---

## 🔁 Using Ngrok with Webhooks

Services like Stripe, GitHub, or Twilio need a public URL to send events.

Example:
```bash
ngrok http 5000
```
Now use the generated public URL as the webhook endpoint.

---

## 🧰 Advanced Features

- **Ngrok Config File:** `~/.ngrok2/ngrok.yml`
```yaml
authtoken: YOUR_TOKEN
tunnels:
  web:
    proto: http
    addr: 3000
    subdomain: myapp
```
Then run:
```bash
ngrok start web
```

- **Inspect Replay:** Replay a previous request:
```bash
curl -X POST http://127.0.0.1:4040/api/requests/http/replay -d 'id=<REQUEST_ID>'
```

---

## 🔐 Security Best Practices

- Avoid exposing sensitive services (e.g., databases) unless absolutely necessary.
- Use authentication (`-auth`) to protect public URLs.
- Don't share your Ngrok token publicly.

---

## 🛠️ Troubleshooting

- **Tunnel not connecting:** Check internet connection and firewall settings.
- **Port already in use:** Use a different local port.
- **403 Forbidden:** Make sure to authenticate properly.

---

## 📚 References

- [Ngrok Official Site](https://ngrok.com/)
- [Ngrok Documentation](https://ngrok.com/docs)
- [Ngrok GitHub](https://github.com/inconshreveable/ngrok)

---

Feel free to fork this README and add more tips as you grow your Ngrok skills! 🚀

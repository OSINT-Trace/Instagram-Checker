# Instagram Account Checker & Intelligence API

[![OSINT Trace - Direct API (Recommended)](https://img.shields.io/badge/OSINT%20Trace-Direct%20API%20(Recommended)-00DF9A?style=for-the-badge&logo=shield)](https://osinttrace.com) [![API.Market](https://img.shields.io/badge/API.Market-8B5CF6?style=for-the-badge)](https://api.market/store/osint-trace-1/instagram-checker) [![RapidAPI](https://img.shields.io/badge/RapidAPI-black?style=for-the-badge&logo=rapidapi)](https://rapidapi.com/osint-org-osint-org-default/api/instagram-checker)

An enterprise-grade OSINT API to verify Instagram account existence and retrieve rich profile intelligence (numerical User IDs, follower/following metrics, post counts, biography, HD avatar URLs, verified badges, account type, and profile links) by username, email address, or phone number.

## Table of Contents
- [Features](#features)
- [Getting Started](#getting-started)
  - [1. Get API Key](#1-get-api-key)
  - [2. Base URL & Authentication](#2-base-url--authentication)
- [API Endpoints](#api-endpoints)
  - [Single Account Check](#single-account-check)
  - [Code Examples](#code-examples)
- [Response Format](#response-format)
- [HTTP Status Codes](#http-status-codes)
- [Requirements](#requirements)
- [Pricing](#pricing)
- [Support](#support)
- [Legal Compliance](#legal-compliance)

---

## Features

✅ **Instant Verification**: Real-time presence verification for Instagram profiles.  
✅ **Multi-Identifier Input**: Accepts usernames, email addresses, and E.164 phone numbers.  
✅ **Deep Metadata Extraction**: Returns numerical User IDs, display names, biographies, follower/following counts, total post counts, verified badges, private account status, business account category, external links, and direct profile URLs.  
✅ **High Performance**: Asynchronous architecture with high-speed proxy cycling and anti-bot bypass.  
✅ **Developer-Friendly**: Available via direct REST API on [OSINT Trace](https://osinttrace.com) (Recommended) and major developer marketplaces.

---

## Getting Started

### 1. Get API Key

- **OSINT Trace Direct (Recommended)**: Create an account on [OSINT Trace](https://osinttrace.com) and generate your API Key from the [Workspace Dashboard](https://app.osinttrace.com).
- **API.Market**: Subscribe via [API.Market Instagram Checker](https://api.market/store/osint-trace-1/instagram-checker).
- **RapidAPI**: Subscribe via [RapidAPI Instagram Checker](https://rapidapi.com/osint-org-osint-org-default/api/instagram-checker).

### 2. Base URL & Authentication

Authentication headers and endpoints vary by provider:

| Provider | Base URL | Auth Header | Endpoint |
|:---|:---|:---|:---|
| **OSINT Trace (Direct - Recommended)** | `https://api.osinttrace.com/v1` | `x-osint-key: YOUR_OSINT_KEY` | `POST /check/instagram` |
| **API.Market** | `https://prod.api.market/api/v1/osint-trace-1/instagram-checker` | `X-Api-Key: YOUR_API_KEY` | `POST /check/instagram` |
| **RapidAPI** | `https://instagram-checker.p.rapidapi.com` | `X-RapidAPI-Key: YOUR_API_KEY`<br>`X-RapidAPI-Host: instagram-checker.p.rapidapi.com` | `POST /check` |

---

## API Endpoints

### Single Account Check

**Endpoint (OSINT Trace Direct - Recommended):**
> `POST https://api.osinttrace.com/v1/check/instagram`

**Request Body:**
```json
{
  "input": "target_username"
}
```

### Code Examples

<details open>
<summary><b>OSINT Trace Direct API (cURL) — Recommended</b></summary>

```bash
curl --request POST \
     --url https://api.osinttrace.com/v1/check/instagram \
     --header 'x-osint-key: YOUR_OSINT_KEY' \
     --header 'Content-Type: application/json' \
     --data '{"input": "target_username"}'
```
</details>

<details>
<summary><b>API.Market (cURL)</b></summary>

```bash
curl --request POST \
     --url https://prod.api.market/api/v1/osint-trace-1/instagram-checker/check/instagram \
     --header 'X-Api-Key: YOUR_API_KEY' \
     --header 'Content-Type: application/json' \
     --data '{"input": "target_username"}'
```
</details>

<details>
<summary><b>RapidAPI (cURL)</b></summary>

```bash
curl --request POST \
     --url https://instagram-checker.p.rapidapi.com/check \
     --header 'X-RapidAPI-Host: instagram-checker.p.rapidapi.com' \
     --header 'X-RapidAPI-Key: YOUR_API_KEY' \
     --header 'Content-Type: application/json' \
     --data '{"input": "target_username"}'
```
</details>

> Additional code snippets for Python, Node.js, Go, PHP, C#, Java, and Shell are available in the [`examples/`](./examples) directory.

---

## Response Format

### Account Found (With Metadata)
```json
{
  "live": true,
  "note": null,
  "metadata": {
    "user_id": "1234567890",
    "username": "cyber_analyst",
    "name": "Alex Smith",
    "bio": "Security Researcher & OSINT Enthusiast 🔍",
    "avatar_url": "https://scontent.cdninstagram.com/v/t51.2885-19/example_avatar.jpg",
    "followers": 12500,
    "following": 340,
    "posts": 87,
    "is_private": false,
    "is_verified": true,
    "is_business": false,
    "category": "Creator",
    "external_url": "https://osinttrace.com",
    "profile_url": "https://www.instagram.com/cyber_analyst"
  }
}
```

### Account Not Found
```json
{
  "live": false,
  "note": null,
  "metadata": null
}
```

---

## HTTP Status Codes

| Status Code | Description | Rationale |
|:---|:---|:---|
| **`200 OK`** | Success | Query processed and presence/metadata returned. |
| **`400 Bad Request`** | Validation Error | Malformed request body or input under minimum length. |
| **`401 Unauthorized`** | Authentication Required | Missing, invalid, or expired API key header. |
| **`403 Forbidden`** | Quota / Subscription Error | Quota balance exhausted or subscription inactive. |
| **`408 Request Timeout`** | Timeout | Upstream verification exceeded maximum execution window. |
| **`429 Too Many Requests`** | Rate Limit Exceeded | Exceeded 1 request/second limit. |

---

## Requirements

- **Minimum input length**: 3 characters
- **Supported input formats**:
  - Usernames (`instagram_user`)
  - Email addresses (`user@example.com`)
  - Phone numbers (E.164 standard recommended: `+1234567890`)
- **Rate Limit**: 1 request per second per active API key.

---

## Pricing

- **Direct Plans (Recommended)**: Flexible subscription tiers and bulk volume pricing available on [OSINT Trace Pricing](https://osinttrace.com/pricing).
- **Marketplace Plans**: Subscriptions also available through [API.Market](https://api.market/store/osint-trace-1/instagram-checker) and [RapidAPI](https://rapidapi.com/osint-org-osint-org-default/api/instagram-checker/pricing).
- **Free Tier**: Free tier available for evaluation and testing.

---

## Support

For technical inquiries, enterprise SLA plans, or integration assistance:  
📧 Email: [support@osinttrace.com](mailto:support@osinttrace.com)  
🌐 Website: [osinttrace.com](https://osinttrace.com)

---

## Legal Compliance

This API is designed for legitimate cybersecurity investigation, fraud prevention, brand monitoring, and threat intelligence. Users must:
- Comply with applicable local and international data protection regulations (e.g., GDPR, CCPA).
- Adhere to Instagram's Terms of Service and acceptable use policies.
- Ensure lawful basis for investigative data processing.

*This service is independently operated by OSINT Trace and is not affiliated with or endorsed by Meta Platforms, Inc. or Instagram.*

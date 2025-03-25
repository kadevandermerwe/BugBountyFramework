# Vulnerability Report Template

## Summary
A concise description of the vulnerability, the component it affects, and its impact.

Example:
Unauthenticated users can exploit a reflected XSS vulnerability in the `/search` endpoint by injecting malicious JavaScript via the `query` parameter.

---

## Target Information

- **URL / Endpoint**: 
- **Method**: 
- **Affected Parameter(s)**: 
- **Authentication Required**: Yes / No
- **User Role (if applicable)**: 

---

## Steps to Reproduce

1. Step-by-step instructions to reproduce the issue manually or with a tool.
2. Include payloads, request/response examples, or browser actions.
3. Clarify any prerequisites or conditions required for exploitation.

---

## Impact

Clearly describe what an attacker can do with this vulnerability.

Example:
- Execute JavaScript in the context of another user (XSS)
- Access sensitive data (IDOR)
- Modify account settings without authorization (CSRF)
- Gain full control of the server (RCE)

---

## Proof of Concept (PoC)

- **Payload**: 
- **Full HTTP Request** (if relevant):
  ```http
  POST /example
  Host: target.com
  Content-Type: application/json

  {
    "parameter": "payload"
  }

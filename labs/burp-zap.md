# Lab 05 — Web Security Testing with Burp Suite and OWASP ZAP

## Aim
Understand how an intercepting proxy supports authorized web application testing.

## Burp Suite workflow
1. Start Burp Suite and use its browser or configure a dedicated test browser.
2. Open a local training application that you control.
3. Use Proxy to inspect a request and response.
4. Send a harmless request to Repeater.
5. Change a benign parameter and resend it.
6. Compare the response and document what changed.

## OWASP ZAP workflow
1. Start ZAP and configure a local training application as the target.
2. Browse the application through ZAP.
3. Review passive scan alerts.
4. Read each alert's evidence and remediation guidance.
5. Use active scanning only on an intentionally vulnerable local lab or a target with explicit written authorization.

## Concepts
- Passive scanning analyses observed traffic without actively sending attack payloads.
- Active scanning sends crafted test requests and may alter application state or affect availability.
- Scanner alerts require manual validation; false positives are possible.

## Safety
Never scan or manipulate third-party websites, accounts or production systems without explicit authorization. Do not include real credentials, session cookies, tokens or personal data in screenshots or reports.

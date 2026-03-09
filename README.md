markdown# 🧘 SpineErectaAI

Real-time posture coach that runs entirely in your browser — no signup, no uploads, no server.
Uses BlazePose to track 33 body landmarks via your camera. See the **[demo](#)**.

## Run locally

1. Download `SpineErectaAI_v7.html`
2. Open in Chrome, Edge, or Safari
3. Allow camera access
4. Complete the health profile wizard
5. Click ▶ Start Analysis

Or serve it:
```
python3 -m http.server 8080
```

## Config

Edit the `CONFIG` object at the top of the file to set your Calendly link, WhatsApp number, or Google Sheets webhook.

## License

MIT — [Disclaimer](#): assistive tool only, not a medical device.

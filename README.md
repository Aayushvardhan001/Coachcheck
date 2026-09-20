# CoachCheck

Self-check kiosk for reserved train coaches. Passengers scan their ticket at the coach door, get verified, and are guided to their seat. TTEs see a live dashboard instead of checking every seat by hand.

> Prototype: uses sample tickets for a fictional train (12345 Demo Express). No real railway data is used.

## Problem
- TTEs spend a lot of time checking tickets seat by seat.
- Passengers sit in wrong coaches or seats, which causes disputes.
- Ticketless travel is hard to catch early.

## Solution
A kiosk at every coach door:
1. Passenger scans the ticket QR (or types the PNR).
2. The system verifies it: valid, right coach, right date, confirmed seat.
3. The screen shows the seat, berth type and bay, and lights up that seat on the coach map (on real hardware: a per-seat LED).
4. Problems (wrong coach, waitlist, cancelled, old date, fake PNR, rescan) are shown clearly and logged for the TTE.

## Features
- QR scanning through the camera (jsQR) or manual PNR entry
- Verification logic for 7 outcomes: OK, wrong coach, duplicate scan, waitlist, cancelled, wrong date, not found
- Sleeper coach map (72 berths, 9 bays) with the passenger's seat lit
- TTE dashboard: per-coach progress, seat states, passenger table, live scan log
- "Simulate boarding" mode for demos
- English and Hindi, plus beep and voice announcements
- Sample QR codes to try each scenario

## Run it
No build step. Open `index.html` (this is `coachcheck.html`) in a browser. Camera scanning needs HTTPS or localhost.

## Tech
HTML, CSS, vanilla JavaScript, jsQR, qrcode-generator.

## Roadmap
- FastAPI + PostgreSQL backend to verify against a real chart
- Offline mode: chart downloaded to the kiosk before departure
- Raspberry Pi / Android kiosk hardware and ESP32-controlled seat LEDs
- Integration with railway systems (needs official permission)

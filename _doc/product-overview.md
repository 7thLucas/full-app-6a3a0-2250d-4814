# Product Overview — FlowPay

## Status
A1 discovery complete. All core fields confirmed from user spec.

## Product Name
FlowPay

## Category
Flutter super app — fintech / digital payments

## Positioning
A clean, minimal Flutter payment super app with real Razorpay UPI integration. No wallets, no fake balances, no stored money logic — only real transactions. Designed as a pluggable service platform that starts with UPI payments and expands into recharge, bills, travel, taxi, food delivery, and courier services.

## Target Users
Mobile-first consumers making digital payments on their phones. Primary use case: UPI payments via Razorpay. Secondary (future): recharge, bill payments, travel, taxi, food delivery.

## Core Problem
Existing payment super apps are bloated with wallet systems, fake cashback logic, and heavy UX. Users need a fast, clean app for real money transactions — no complexity, no fake balance mechanics, just a direct path from service selection to Razorpay checkout.

## Day-One Feature (North Star)
**UPI Payment Flow:**
Home Screen → tap "UPI Payment" from service grid → PaymentScreen (enter amount, Pay Now) → Razorpay Checkout (amount × 100 paise, placeholder Key ID, success/error callbacks) → ResultScreen (Success with Payment ID / Failed status).

## Screens
- **HomeScreen**: Card-based service grid — UPI Payment (active), Recharge, Bills, Services, Travel, More (all placeholders except UPI). Modern card UI.
- **PaymentScreen**: Amount input field + "Pay Now" button. Initializes Razorpay, handles PAYMENT_SUCCESS and PAYMENT_ERROR, disposes on exit.
- **ResultScreen**: Centered UI — payment status (Success / Failed), Payment ID if available. No extra buttons or logic.

## Architecture
```
main.dart
screens/
services/
widgets/
models/
```
Clean separation of UI and payment logic. Each service is a pluggable module — adding taxi, food, courier, or utility APIs must not require redesigning the core app.

## Razorpay Integration
- Package: `razorpay_flutter`
- Amount conversion: amount × 100 (paise)
- Key: placeholder Razorpay Key ID
- Events: PAYMENT_SUCCESS → ResultScreen with payment ID; PAYMENT_ERROR → ResultScreen with failed status
- Lifecycle: Initialize on PaymentScreen, dispose on screen exit

## Brand & Tone
Minimal, modern fintech UI. Card-based layouts. Simple navigation. No animation overload. Fast performance. Play Store ready structure.

## Business Rules (STRICT)
- No wallet system
- No fake balance or cashback
- No stored money logic
- Only real Razorpay transactions
- Service payment app only

## Scalability
Pluggable architecture. Future services to add without core redesign:
- Taxi booking APIs
- Food delivery APIs
- Courier services
- Utility bill payments

## Platform
Flutter (mobile) — Play Store ready structure.

---
_Last updated: full spec confirmed — FlowPay UPI payment super app._

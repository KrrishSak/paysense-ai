# PaySense AI 💳

> An AI-powered payment intelligence tool built with Claude — ask questions about payments, analyze transactions, and classify spending at scale.

![PaySense AI Demo](https://img.shields.io/badge/Status-Live-brightgreen) ![Claude Powered](https://img.shields.io/badge/Powered%20by-Claude%20AI-blue) ![Domain](https://img.shields.io/badge/Domain-Fintech%20%2F%20Payments-orange)

---

## What It Does

PaySense AI is a three-feature fintech tool that uses large language models to make payment data more intelligible for users and businesses.

**Feature 1 — Payment Support Assistant**
A conversational AI trained on the context of Indian payments infrastructure. Ask it anything:
- Why did my UPI payment fail?
- What is the T+1 settlement cycle?
- How do payment gateway fees work?
- What is PCI DSS compliance and why does it matter?

No documentation lookup. No Google. Just instant, accurate answers.

**Feature 2 — Transaction Analyzer**
Paste in a set of bank transactions and get a structured AI analysis:
- Spending breakdown by category
- Key observations and patterns
- Anomaly detection and flags
- Financial health score with reasoning

**Feature 3 — Bulk Transaction Classifier**
Paste raw bank transaction strings (the kind you get from a statement export) and get every line categorized instantly. Categories include: Food & Dining, Shopping, Travel, Utilities, Salary, Loan / EMI, ATM Withdrawal, Freelance, Healthcare, Investment.

---

## Why I Built This

I wanted to build something at the intersection of AI and real-world fintech — a domain where the complexity of Indian payment infrastructure (UPI, NACH, IMPS, NEFT, RTGS, POS) creates genuine friction for users and businesses.

Most people don't understand why payments fail, what settlement cycles mean, or how to read a raw bank statement. This project uses LLMs to close that gap — turning opaque financial data into clear, actionable intelligence.

The problem is real. The use case is real. The AI isn't a gimmick here — it's the core of the product.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JS |
| AI Engine | Claude claude-sonnet-4-20250514 (Anthropic API) |
| API | Anthropic `/v1/messages` |
| Hosting | Static — runs in any browser |

---

## How to Run

**Option 1 — Open directly**
Clone the repo and open `index.html` in any browser. No build step required.

```bash
git clone https://github.com/KrrishSak/paysense-ai
cd paysense-ai
open index.html
```

**Option 2 — With API key**
The app calls the Anthropic API. You will need an API key set up:
1. Get a key at [console.anthropic.com](https://console.anthropic.com)
2. The key is handled via the Anthropic proxy in the hosted version

---

## Features Breakdown

```
PaySense AI
├── Payment Assistant
│   ├── Suggested questions (UPI, refunds, compliance)
│   ├── Multi-turn conversation with memory
│   └── Grounded in Indian payments context (RBI, NPCI, Razorpay)
│
├── Transaction Analyzer
│   ├── Auto-categorizes transactions client-side
│   ├── Calculates debit/credit totals
│   └── Sends to Claude for deep financial analysis
│
└── Bulk Classifier
    ├── Accepts raw bank transaction strings
    ├── Returns structured JSON categories
    └── Handles NEFT, UPI, NACH, POS, ATM formats
```

---

## Sample Output

**Bulk Classifier Input:**
```
NEFT/Amazon Pay
UPI/swiggy@upi
ATM WDL 9876
NACH EMI HDFC
IRCTC TICKET BKG
```

**AI Output:**
```json
[
  { "desc": "NEFT/Amazon Pay", "category": "Shopping", "type": "debit" },
  { "desc": "UPI/swiggy@upi", "category": "Food & Dining", "type": "debit" },
  { "desc": "ATM WDL 9876", "category": "ATM Withdrawal", "type": "debit" },
  { "desc": "NACH EMI HDFC", "category": "Loan / EMI", "type": "debit" },
  { "desc": "IRCTC TICKET BKG", "category": "Travel", "type": "debit" }
]
```

---

## What I Learned

- How to engineer prompts for structured JSON output from LLMs — and handle edge cases where the model doesn't return clean JSON
- How to design multi-turn conversation state management without a backend (full history passed on every call)
- The complexity of Indian payment rails — UPI mandate flows, NACH cycles, POS vs IMPS vs NEFT settlement differences
- How to build AI-powered interfaces that feel native and fast, not bolted on

---

## What's Next

- [ ] Connect to real bank statement CSV uploads (parse and analyze full months)
- [ ] Add Razorpay webhook simulation — classify incoming payment events in real time
- [ ] Build a merchant dashboard layer — categorize payouts, refunds, disputes
- [ ] Add voice input for payment queries
- [ ] Anomaly detection model trained on fraud patterns in UPI transactions

---

## About

Built by **Krish Sakhuja** as a proof-of-work project demonstrating applied AI in fintech.

- GitHub: [github.com/KrrishSak](https://github.com/KrrishSak)
- LinkedIn: [linkedin.com/in/krissh-sakhuja](https://www.linkedin.com/in/krissh-sakhuja/)
- Email: krisshsakhuja66@gmail.com

---

*Built for the intersection of AI and payments infrastructure. If you're working on something in this space, let's talk.*

# AccordPay AI

### Agree First. Pay With Confidence.

**An AI-assisted B2B invoice dispute resolution platform combining price intelligence, evidence-based analysis, structured negotiation, and PayPal Sandbox payments.**

**Built for the PayPal AI Hackathon 2026**

---

## Overview

AccordPay AI addresses a common challenge in business transactions: **what happens when a buyer disagrees with a seller's invoice?**

Instead of relying on lengthy email exchanges, manual price comparisons, and unstructured negotiations, AccordPay AI brings the dispute resolution process into one unified platform.

The application enables businesses to compare supplier invoices against vendor price references, analyze discrepancies, negotiate settlements, and complete mutually approved payments through PayPal.

**Our mission is simple: Help businesses reach an agreement before money changes hands.**

## The Problem

Invoice disagreements can delay payments and damage business relationships.

Consider a buyer who receives an invoice for $899 for a product that comparable vendors advertise at lower prices.

The buyer needs to determine whether the difference is justified, communicate the concern, and negotiate an acceptable price.

Traditional workflows often require multiple tools and conversations, with limited transparency into how a settlement was reached.

## Our Solution

AccordPay AI connects invoice review, price analysis, negotiation, and payment into a single workflow.

**Invoice → Market Comparison → AI-Assisted Review → Negotiation → Mutual Agreement → PayPal Payment**

The platform is designed to assist both parties rather than automatically decide who is right.

## Core Features

### 1. Invoice Management

- Create and review invoice dispute cases.
- Record product details, quantities, and supplier charges.
- Track the status of each dispute.
- Access a dedicated negotiation workspace.

### 2. Transparent Price Intelligence

AccordPay AI provides a calculation engine for comparing invoices with vendor quotations.

Users can enter:

- Product specifications and quantity.
- Vendor names and unit prices.
- Source URLs for reference.
- Applicable tax percentages and additional costs.

The system calculates:

- Median vendor unit price.
- Quantity-adjusted market benchmark.
- Invoice-to-benchmark difference.
- Percentage difference and potential savings.

**Market prices are currently entered by users, not automatically verified or retrieved.** The calculations use the provided numerical inputs.

### 3. Google Gemini AI Analysis

AccordPay AI integrates Google Gemini to review invoice disputes and supporting evidence.

The AI can:

- Examine invoice discrepancies.
- Review supplied agreements and buyer statements.
- Identify potentially unsupported charges.
- Suggest a possible settlement amount.
- Highlight missing evidence.

AI-generated findings are advisory. Both parties retain control over the final agreement.

### 4. Negotiation Engine

The buyer and seller can:

- Submit settlement offers.
- Respond with counteroffers.
- Explore midpoint suggestions.
- Review negotiation history.
- Accept a mutually agreed amount.

The platform records the negotiation process to provide an auditable sequence of actions.

### 5. PayPal Sandbox Checkout

Once both parties agree, AccordPay AI integrates with PayPal's Sandbox APIs to demonstrate the payment process.

The integration supports:

- Creating a PayPal checkout order.
- Redirecting the buyer for payment approval.
- Verifying the order status.
- Capturing an approved Sandbox payment.
- Recording the payment result.

**No real money is transferred during Sandbox testing.**

### 6. Calculation-Based Fallback

If Gemini is unavailable because of API quotas or connectivity issues, the platform can use transparent, rule-based calculations for supported invoice comparisons.

The fallback does not impersonate an AI-generated result.

---

## Demonstration Scenario

A supplier invoices a buyer $899 for an iPhone 16.

The buyer enters two illustrative vendor quotations:

| Item | Amount |
|---|---:|
| Supplier invoice | $899 |
| Vendor A reference price | $829 |
| Vendor B reference price | $699 |
| Calculated median benchmark | $764 |
| Invoice above benchmark | $135 |

**Benchmark calculation:**

($829 + $699) ÷ 2 = $764

**Invoice difference:**

$899 − $764 = $135

The buyer can then raise a dispute, review the evidence, and negotiate with the seller.

These reference prices are illustrative inputs rather than independently verified live offers. Actual comparisons should use matching product specifications and applicable costs.

---

## Technology Stack

| Layer | Technology |
|---|---|
| Backend | Python, FastAPI |
| Frontend | HTML, CSS, JavaScript |
| Database | SQLite |
| AI Analysis | Google Gemini API |
| HTTP Integration | HTTPX |
| Payment Processing | PayPal REST APIs (Sandbox) |
| Configuration | Python Dotenv |

## Architecture

```text
              BUYER / SELLER
                    |
                    v
          INVOICE DASHBOARD
                    |
                    v
          PRICE COMPARISON
                    |
                    v
       MATHEMATICAL BENCHMARK
                    |
                    v
          DISPUTE SUBMISSION
                    |
                    v
           GEMINI AI ANALYSIS
          /                  \
    AI Available         AI Unavailable
          |                    |
    AI Recommendation    Rule-Based Review
          \                  /
                    |
                    v
            NEGOTIATION ENGINE
                    |
                    v
             MUTUAL AGREEMENT
                    |
                    v
           PAYPAL SANDBOX API
                    |
                    v
           PAYMENT VERIFICATION
```

## Run Locally — Instructions for Judges

The application is currently provided as a locally runnable prototype. It is not hosted at a public production URL.

### Prerequisites

- Python 3.10 or newer
- Internet access for Gemini and PayPal integrations
- Optional Google Gemini API key for AI analysis
- PayPal Sandbox API credentials for payment testing

### Step 1 — Clone the Repository

```bash
git clone https://github.com/sanjivinsmoke33/AccordPay-AI.git
cd AccordPay-AI
```

### Step 2 — Create a Virtual Environment

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
source .venv/bin/activate
```

### Step 3 — Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### Step 4 — Configure API Credentials

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=
GEMINI_MODEL=gemini-2.5-flash

PAYPAL_CLIENT_ID=
PAYPAL_CLIENT_SECRET=
```

Use a supported Gemini model available to the configured API project.

The billing interface, manual price comparisons, and arithmetic calculations can be demonstrated without API credentials.

Gemini analysis and PayPal Sandbox transactions require their respective credentials.

**Do not commit API keys or credentials to the repository.**

### Step 5 — Launch the Application

```bash
python -m uvicorn main:app --reload
```

Open the application in a browser:

http://127.0.0.1:8000

Interactive API documentation:

http://127.0.0.1:8000/docs

These are local development URLs, accessible on the computer running the server.

---

## Suggested Evaluation Workflow

Judges can evaluate AccordPay AI through the following sequence:

1. Launch the application and open the billing dashboard.
2. Create an invoice case with a supplier amount and product specifications.
3. Enter two or more vendor reference prices.
4. Calculate the benchmark and inspect the resulting price difference.
5. Open the dispute negotiation workspace.
6. Raise an issue as the buyer.
7. Review Gemini analysis when configured, or the available calculation-based fallback.
8. Submit a seller proposal and respond as the buyer.
9. Reach mutual agreement.
10. Test the PayPal Sandbox checkout flow using valid Sandbox accounts.

**Important:** Buyer and seller role switching is simulated in the prototype. It is not a production authentication system.

## Design Philosophy

AccordPay AI is built around three principles:

**Transparency:** Make invoice discrepancies and calculations understandable.

**Mutual consent:** Keep final settlement decisions with the buyer and seller.

**Payment confidence:** Initiate payment only after agreement.

## Current Limitations

This project is a hackathon prototype and is not intended for production financial transactions.

- Vendor prices are manually entered and not independently verified.
- Gemini analysis depends on API availability and quota.
- Buyer and seller roles do not yet have secure authentication.
- The platform does not provide escrow or legally binding arbitration.
- PayPal transactions are demonstrated using Sandbox accounts.
- Production deployment would require additional security, compliance, authorization, and operational safeguards.

## Future Development

Planned improvements include:

- Live market pricing through supported retailer and supplier APIs.
- PDF invoice and purchase order extraction.
- AI-assisted product specification matching.
- Secure buyer and seller authentication.
- Real-time negotiation notifications.
- Supplier price history and analytics.
- Production-ready payment workflows.

## Project Repository

**GitHub:** https://github.com/sanjivinsmoke33/AccordPay-AI

## License

Licensed under the MIT License. See the `LICENSE` file for details.

---

### AccordPay AI

**Agree First. Pay With Confidence.**

*Making invoice disputes more transparent, negotiations more structured, and payments more confident.*

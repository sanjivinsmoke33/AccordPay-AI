# AccordPay AI

### Agree First. Pay With Confidence.

**An AI-assisted invoice dispute resolution and negotiation platform powered by Google Gemini and PayPal.**

AccordPay AI helps buyers and sellers resolve invoice disagreements through transparent price comparisons, evidence-based analysis, structured negotiation, and mutually agreed payments.

Instead of arguing over unexpected charges, both parties can review the numbers, negotiate a fair settlement, and complete payment through PayPal Sandbox.

## The Problem

Invoice disputes create friction between buyers and sellers.

A supplier may charge more than a buyer expects, leading to delayed payments, disagreements, and damaged business relationships.

Traditional dispute resolution can be slow, expensive, and difficult for small businesses.

## Our Solution

AccordPay AI provides a structured workflow that helps both parties understand and resolve billing disagreements.

**Billing Review → Price Comparison → AI Analysis → Negotiation → Agreement → Payment**

The platform combines real mathematical calculations with AI-assisted analysis to make invoice disputes more transparent.

## Key Features

### 1. Smart Billing Dashboard

- Create and manage invoice dispute cases.
- Review supplier invoices and buyer assessments.
- View invoice status and disputed amounts.
- Navigate directly to individual negotiation cases.

### 2. Market Price Intelligence

- Compare product prices from multiple vendor quotations.
- Enter vendor names, unit prices, and source URLs.
- Calculate the median benchmark price.
- Account for quantity, tax, and additional costs.
- Identify invoice amounts above the calculated benchmark.

**Note:** Vendor prices are currently supplied by the user. The platform does not independently verify live market prices.

### 3. Gemini AI Invoice Analysis

- Analyze disputed invoice charges.
- Review supplied agreements and supporting evidence.
- Identify potentially unsupported charges.
- Recommend possible settlement amounts.
- Highlight missing evidence.

AI recommendations are advisory. Final decisions remain with the buyer and seller.

### 4. Buyer–Seller Negotiation

- Submit offers and counteroffers.
- Suggest midpoint settlements.
- Record negotiation history.
- Require mutual agreement before payment.

### 5. PayPal Sandbox Integration

- Create PayPal Sandbox checkout orders.
- Allow buyers to approve payment.
- Verify PayPal order status.
- Capture approved payments.
- Record payment results.

Sandbox transactions use test accounts and do not transfer real money.

### 6. Transparent Calculation Fallback

When Gemini is unavailable, AccordPay AI can provide rule-based invoice comparisons and mathematical settlement calculations.

These calculations are clearly distinguished from AI-generated analysis.

## Example Use Case

A company receives an invoice for an Apple iPhone 16.

| Description | Amount |
|---|---:|
| Supplier invoice | $899 |
| Vendor A price (illustrative) | $829 |
| Vendor B price (illustrative) | $699 |
| Median benchmark | $764 |
| Invoice above benchmark | $135 |

**Calculation:**

Median benchmark = ($829 + $699) / 2 = $764

Invoice difference = $899 − $764 = $135

The buyer can use this comparison to raise a dispute and begin negotiation.

The prices above illustrate the calculation and are not presented as verified live quotations.

## Technology Stack

| Component | Technology |
|---|---|
| Backend | Python, FastAPI |
| Frontend | HTML, CSS, JavaScript |
| Database | SQLite |
| AI | Google Gemini API |
| Payments | PayPal REST APIs (Sandbox) |
| HTTP client | HTTPX |
| Configuration | Python Dotenv |

## Getting Started

### Prerequisites

- Python 3.10 or newer
- Internet connection for external APIs
- Google Gemini API key for AI analysis
- PayPal Developer Sandbox credentials for payment testing

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/AccordPay-AI.git
cd AccordPay-AI
```

Replace `YOUR_USERNAME` with your GitHub username.

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

Activate on Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the project root.

```env
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=gemini-2.5-flash

PAYPAL_CLIENT_ID=your_sandbox_client_id
PAYPAL_CLIENT_SECRET=your_sandbox_client_secret
```

Choose a Gemini model available to your API project.

Never commit your actual `.env` file or API credentials to GitHub.

### 5. Run the Application

```bash
python -m uvicorn main:app --reload
```

Open:

http://127.0.0.1:8000

API documentation:

http://127.0.0.1:8000/docs

## How to Test

1. Open the billing dashboard.
2. Create an invoice case with product details and supplier charges.
3. Enter comparable vendor prices and calculate the benchmark.
4. Open the dispute and negotiation workspace.
5. Raise an issue as the buyer.
6. Analyze the evidence using Gemini, or use the calculation-based fallback when available.
7. Submit a seller proposal.
8. Accept the proposal or negotiate a counteroffer.
9. Reach mutual agreement.
10. Complete the PayPal Sandbox checkout workflow.

For payment testing, use PayPal Sandbox buyer and seller accounts.

## System Architecture

```text
Buyer / Seller
      |
      v
Billing Dashboard
      |
      v
Vendor Price Comparison
      |
      v
Calculation Engine
      |
      v
Invoice Dispute
      |
      v
Gemini AI Analysis
(or rule-based fallback)
      |
      v
Negotiation Engine
      |
      v
Mutual Agreement
      |
      v
PayPal Sandbox Checkout
      |
      v
Payment Verification
```

## Security and Limitations

AccordPay AI is a hackathon prototype.

- Buyer and seller roles are demonstrated without production authentication.
- Market prices are manually entered and are not automatically verified.
- AI analysis may be unavailable when API quotas are exhausted.
- AI recommendations are not legally binding.
- PayPal integration uses Sandbox credentials and test payments.
- Production use would require authentication, authorization, secure document storage, audit protections, and additional payment safeguards.

## Future Roadmap

- Automated market price retrieval from supported vendor APIs.
- PDF invoice and purchase order uploads.
- AI-assisted line-item matching.
- Secure buyer and seller accounts.
- Real-time negotiation notifications.
- Supplier reputation and historical pricing insights.
- Production-ready payment and compliance integrations.

## Why AccordPay AI?

AccordPay AI brings together three important capabilities:

**Price transparency + Assisted negotiation + Payment integration**

Our goal is to make invoice disputes easier to understand, faster to negotiate, and simpler to resolve.

## Hackathon Project

Built for the **PayPal AI Hackathon 2026**.

This project demonstrates how AI-assisted analysis and PayPal payment technology can work together to improve commercial transactions.

## License

This project is released under the MIT License. See the `LICENSE` file for details.

---

**AccordPay AI — Agree First. Pay With Confidence.**.

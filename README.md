# Stripe Net Payout Calculator

A modern, high-precision tool to calculate the exact amount to charge a customer to ensure you receive a specific net payout after Stripe's processing fees, supporting variable payout schedules (Standard, Next-Day, and Instant).

This tool is designed for freelancers, MSPs, and small businesses who need to pass on credit card fees transparently and accurately while managing cash flow speeds.

## ✨ Features

- **Glassmorphism UI**: A sleek, modern "frosted glass" interface that looks great on any background.
- **System Theme Support**: Automatically switches between Light and Dark modes based on user OS settings.
- **Dynamic Payout Schedules**: Accounts for standard processing alongside premium delivery tiers:
  - **Standard**: Base processing rate (2.9% + $0.30).
  - **Next-Day**: Optimized next-day payout routing (+0.6%).
  - **Instant Payouts**: Real-time funds transfer (+1.5% with an integrated $0.50 minimum check).
- **Threshold-Aware Logic**: Uses custom reverse-math formulas that automatically detect if an Instant Payout falls under Stripe's $0.50 minimum fee cap, shifting processing logic gracefully between percentage and flat-rate math.
- **Detailed Breakdown**: Shows a 4-step logic path including:
  - Base subtotal and premium speed fee grouping.
  - Combined percentage fee scaling.
  - **Rounding Variance**: Tracks the fractional-cent difference between raw math and banking reality.
- **One-Click Copy**: Quickly copy the Surcharge amount to your clipboard for invoicing.
- **Zero Dependencies**: Pure HTML/CSS/JS. No frameworks, no tracking, no bloat.

## 🌐 Demo Site

Try it live at: [https://surcharge.jpps.us](https://surcharge.jpps.us)

## 🧮 The Math

Most people mistakenly add processing percentages directly to their target price. However, because Stripe takes its percentage from the *final charged total*, standard addition leaves you short. This tool relies on an inverted formula:

$$Total = \frac{Net + FixedFee}{1 - PercentageRate}$$

### ⚡ Instant Payout Edge Case Handling
For Instant Payouts, Stripe levies an extra 1.5% with a minimum charge of $0.50. The tool evaluates the target payout size dynamically:
- **Under the threshold:** The $0.50 minimum is treated as an additional flat fee alongside the standard $0.30 base fee ($0.80 total fixed), evaluated at the standard 2.9% rate.
- **Above the threshold:** The premium percentage is stacked directly onto the processing rate (4.4% total rate) with a standard $0.30 fixed fee.

## 💻 Usage

1. Clone or download this repo.
2. Open `index.html` in any modern web browser.
3. Enter your target payout, pick your payout timeline from the dropdown, and view the results instantly.

## 📦 File Structure

```text
index.html       # Main calculator interface & dropdown logic
README.md        # Project documentation

# Stripe Net Payout Calculator

A modern, high-precision tool to calculate the exact amount to charge a customer to ensure you receive a specific net payout after Stripe's processing fees (2.9% + $0.30).

This tool is designed for freelancers, MSPs, and small businesses who need to pass on credit card fees transparently and accurately.

## ✨ Features

- **Glassmorphism UI**: A sleek, modern "frosted glass" interface that looks great on any background.
- **System Theme Support**: Automatically switches between Light and Dark modes based on user OS settings.
- **Precision Logic**: Uses reverse-math formulas to account for fees being taken from the *total* charge, not the net.
- **Detailed Breakdown**: Shows a 4-step logic path including:
  - Base subtotal calculation.
  - Percentage fee scaling.
  - **Rounding Variance**: Tracks the fractional-cent difference between math and banking reality.
- **One-Click Copy**: Quickly copy the Surcharge amount to your clipboard for invoicing.
- **Zero Dependencies**: Pure HTML/CSS/JS. No frameworks, no tracking, no bloat.

## 🌐 Demo Site

Try it live at: [https://surcharge.jpps.us](https://surcharge.jpps.us)

## 🧮 The Math

Most people mistakenly add 2.9% to their target price, but because Stripe takes 2.9% of the *final* total, you end up short. This tool uses the correct formula:

$$Total = \frac{Net + 0.30}{1 - 0.029}$$



## 💻 Usage

1. Clone or download this repo.
2. Open `index.html` in any modern web browser.
3. Enter your target payout and view the results instantly.

## 📦 File Structure

```text
index.html       # Main calculator interface & Logic
README.md        # Project documentation

```

## 🔧 Customization

You can easily update the fee rates at the top of the `<script>` tag in `index.html`:

```javascript
const STRIPE_FEE_RATE = 0.029; // 2.9%
const STRIPE_FIXED_FEE = 0.30; // $0.30

```

## 📜 License

This project is licensed under the MIT License. Feel free to use, modify, and share.

## 🙋‍♂️ Author

Created by [Jeff Parrish PC Services](https://github.com/4jpps)

Independent MSP specializing in IT solutions, automation, and client-friendly support flows.

```

### Key Additions to your README:
* **Visual Interest**: Added emojis and a `text` block for the file structure to make it scannable.
* **The Math Section**: Added the LaTeX formula and an image placeholder to explain why this tool is better than a standard "add 3%" calculator.
* **Configuration Note**: Mentioned the `STRIPE_FEE_RATE` constant so other developers know how to tweak it for international rates (like 1.4% for UK/EU).

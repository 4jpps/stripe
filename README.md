# Stripe Net Payout Calculator

Calculates how much to charge a customer so that you receive a specific net payout after Stripe's processing fees. It covers the three payout schedules: Standard, Next-Day and Instant.

It is meant for freelancers, MSPs and small businesses who pass card fees on to the customer and want the surcharge worked out exactly.

## Features

- **Light and dark:** The page follows your operating system's light or dark setting.
- **Payout schedules:** Pick one from the dropdown.
  - **Standard:** 2.9% + $0.30.
  - **Next-Day:** adds 0.6%.
  - **Instant:** adds 1.5%, with a $0.50 minimum fee.
- **Instant minimum fee:** For small payouts where 1.5% would come to less than $0.50, the calculator adds the $0.50 as a flat fee instead. Larger payouts use the percentage.
- **Shows its work:** Lists the steps from net payout to final charge, plus the rounding difference in fractions of a cent.
- **Copy button:** Copies the surcharge amount to the clipboard for invoicing.
- **No dependencies:** One HTML file of plain HTML, CSS and JavaScript, with no frameworks and no tracking.
- **Private:** It is a single static page. Nothing you enter is sent anywhere.

## Fee rates

The rates above are hard-coded in `index.html`, not read from Stripe. They were last checked against Stripe's pricing in October 2026. If Stripe changes its fees, update the numbers in `index.html` before relying on the results for invoices.

## Demo site

Try it live at: [https://surcharge.jpps.us](https://surcharge.jpps.us)

## The math

Most people mistakenly add processing percentages directly to their target price. However, because Stripe takes its percentage from the *final charged total*, standard addition leaves you short. This tool relies on an inverted formula:

$$Total = \frac{Net + FixedFee}{1 - PercentageRate}$$

### Instant payout edge case
For Instant Payouts, Stripe levies an extra 1.5% with a minimum charge of $0.50. The tool evaluates the target payout size dynamically:
- **Under the threshold:** The $0.50 minimum is treated as an additional flat fee alongside the standard $0.30 base fee ($0.80 total fixed), evaluated at the standard 2.9% rate.
- **Above the threshold:** The premium percentage is stacked directly onto the processing rate (4.4% total rate) with a standard $0.30 fixed fee.

## Usage

1. Clone or download this repo.
2. Open `index.html` in any modern web browser.
3. Enter your target payout, pick your payout timeline from the dropdown, and view the results instantly.

## File structure

```text
index.html       # Main calculator interface & dropdown logic
README.md        # Project documentation
LICENSE          # MIT license
CNAME            # Custom domain name (surcharge.jpps.us)
```

## License

MIT. See [LICENSE](LICENSE).

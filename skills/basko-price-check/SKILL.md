---
name: basko-price-check
description: Checks whether a grocery or pharmacy price is a good one, using Basko's prices across stores, the 3-month price history and current deals. Use when someone asks "is this a good price", "where is X cheapest", "should I buy now or wait", or shares a price, a shelf photo or a product link from a store in Uzbekistan, Kazakhstan, Russia, the United States or the United Kingdom.
license: MIT
metadata:
  author: BEKRZ MCHJ
  homepage: https://basko.app/en/ai
---

# Price check with Basko

Basko's tools return real prices from stores in five countries, with history. Every number in
your answer must come from them.

The tools you need: `search_products`, `get_product`, `get_deals` (names may carry a prefix
such as `basko` in your client).

## 1. Identify the product

- From a name, a photo of a shelf or a price tag, or a store link: read the brand, the product
  and the size. If the photo is unclear, say what you can read and ask about the rest.
- Country: from the store, currency or conversation (UZ, KZ, RU, US, UK). Ask if nothing says.
- `search_products` with the brand, product and size, then `get_product` on the best match.
  If the size differs from what the person saw, compare per unit (per kg, per litre, per
  tablet) and say you did.

## 2. Judge the price

Compare the price the person has (if they gave one) with:

- **The cheapest store now**, and how far the others are from it.
- **The 3-month range**: is today near the low, the middle or the high?
- **Deals**: is it on a deal now (`get_deals`), and how good is it?

Then give one clear verdict:

- **Good price**: at or near the cheapest now and near the 3-month low.
- **Cheaper elsewhere**: name the store and the difference.
- **Could wait**: only when the history shows this product often drops below today's price.
  Say how often and how far, from the history; never predict beyond what the data shows.
- **Not enough data**: when Basko has the product at one store only, or little history.

## 3. Answer

Lead with the verdict in one sentence, then the two or three numbers behind it, then the
store links exactly as the tools return them (they go through basko.app; don't build store
URLs yourself). Mention the as-of time if it's more than a day old. Add one short line: Basko
may earn a commission from some stores, and it never changes the order.

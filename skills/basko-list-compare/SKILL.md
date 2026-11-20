---
name: basko-list-compare
description: Compares a shopping list across stores with Basko's real prices and finds the cheapest store, the best two-store split and cheaper swaps. Use when someone pastes or dictates a shopping list, shares a photo of a handwritten list or a receipt, or asks where to buy a list of groceries or medicines in Uzbekistan, Kazakhstan, Russia, the United States or the United Kingdom.
license: MIT
metadata:
  author: BEKRZ MCHJ
  homepage: https://basko.app/en/ai
---

# Compare a list with Basko

Basko's tools return real prices from stores in five countries. Use them for every price;
never estimate one.

The tools you need: `search_products`, `compare_basket`, `find_swaps`, `find_stores` (names
may carry a prefix such as `basko` in your client).

## 1. Read the list

- Accept any form: one item per line, commas, "2 bread, milk x3", a photo of a handwritten
  list, or a receipt to re-price. Keep the quantities; default to 1.
- Country from the conversation, currency or store names (UZ, KZ, RU, US, UK). Ask if nothing
  says.
- Answer in the person's language and pass it as `lang`.

## 2. Match and compare

1. `search_products` for each item. When an item is vague ("milk"), pick the everyday choice
   (the most common size and fat level in that country) and say which you picked, so the
   person can change it.
2. `compare_basket` with the matched products and quantities: the total at each store, the
   cheapest single store, and the best split.
3. `find_swaps` for the lines that cost the most, and offer only swaps that do the same job.
4. `find_stores` only if the person asks where the store is, or gives a place: then name the
   nearest branches and their hours.

Items with no match stay on the list, marked "not found in Basko", and are left out of every
total. Say how many were left out.

## 3. Answer

- A short table: store, how many of the items it has, total. Cheapest first. A store missing
  items is not "cheapest" just because its total is lower: say what's missing.
- The best split, if it saves a meaningful amount over the cheapest single store.
- The swaps worth making, with what each saves.
- Store links exactly as the tools return them (they go through basko.app); don't build store
  URLs yourself.
- One short line: Basko may earn a commission from some stores, and it never changes the order.

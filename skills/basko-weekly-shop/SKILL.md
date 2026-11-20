---
name: basko-weekly-shop
description: Plans meals for a week (or a few days, or one dish for a group) and turns them into a priced shopping list at the cheapest store, with real prices from Basko. Use when someone wants a meal plan, a weekly shop, groceries for a recipe or a party, or to feed a household on a budget in Uzbekistan, Kazakhstan, Russia, the United States or the United Kingdom.
license: MIT
metadata:
  author: BEKRZ MCHJ
  homepage: https://basko.app/en/ai
---

# Weekly shop with Basko

Basko's tools return real prices from stores in five countries. Use them for every price you
show: never estimate or remember a price.

The tools you need: `search_products`, `compare_basket`, `find_swaps`, and `get_deals`
(names may carry a prefix such as `basko` in your client).

## 1. Settle the basics

Find out, or infer from the conversation, before you plan:

- **Country**: UZ, KZ, RU, US or UK (`country` on every tool). A city, currency or store
  name usually tells you. If nothing does, ask; don't assume.
- **People and meals**: how many people, which meals (dinners only is common), how many days.
- **Budget, diet and dislikes**, if they mention them. Don't interrogate: two short questions
  at most, then plan with sensible defaults and say what you assumed.

Answer in the person's language and pass it as `lang` (for example `uz`, `ru`, `en`).

## 2. Plan the meals

- Dishes people in that country actually cook (plov and shurpa in Uzbekistan, beshbarmak in
  Kazakhstan, borscht and grechka in Russia, and so on), unless the person asks otherwise.
- Reuse ingredients across days so less is wasted, and say so.
- Keep it short: one line per day.

## 3. Build the list

Turn the meals into one ingredient list with quantities for the whole period (sum repeats:
two dishes with onions means one line of onions). Skip what most kitchens already have (salt,
oil, spices) unless the person says their kitchen is empty; list those as "check you have".

## 4. Price it

1. `search_products` for each ingredient, in the country's language when that finds more
   (Uzbek or Russian names in Uzbekistan, Russian in Russia and Kazakhstan). Pick a product of
   a sensible size for the quantity.
2. `compare_basket` with the chosen products to get the total at each store, the cheapest
   single store, and the best split if buying at two stores saves enough to matter.
3. `find_swaps` when the total is over budget or a line is expensive.
4. `get_deals` if the person is flexible: a dish built around this week's deals can cost less.

If an ingredient has no match, say so plainly and leave it unpriced. Never fill the gap with
a guess.

## 5. Answer

- The meal plan (one line per day).
- The list grouped by store, with each line's price and the total; the cheapest store first.
- What the split saves, if anything, and the swaps that would save the most.
- Store links exactly as the tools return them (they go through basko.app). Don't build or
  shorten store URLs yourself.
- Prices are as of the time the tool shows; say so if they're more than a day old.
- One short line: Basko may earn a commission from some stores, and it never changes the order.

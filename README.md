# Super Budget

I made this for myself because I kept walking into the supermarket with a number in my head and walking out with a different one on the receipt. Super Budget is a small web app for grocery trips. Before I go, I type in a budget. While I shop, I add what goes in the basket, and the app tells me how much I've spent and how much I have left, and it nags me a bit before I get there.

It's a personal project, so it's private and it's built for one person: me.

## What it does

When I start a trip I pick a currency, set the budget and, if I feel like it, write the store name. The budget is always typed fresh. The app only shows my last one as a small suggestion I can tap, because I don't want it quietly reusing a number from three weeks ago.

Items go into the basket two ways. I can tap something I've bought before, and it comes in with the last price I paid. Or I add something new by hand, with a name, a price, a quantity and a category, and the app remembers it for next time. If I want, I can take a photo of the item right there with the phone camera.

At the top of the basket I always see the budget, what I've spent and what's left, with a bar underneath. It's green for a while, turns orange once I'm past 70%, and goes red if I go over. From 80% I get a gentle warning, and if I blow the budget it says by how much. It never stops me from buying anything. It just makes sure I know.

When I'm done, the checkout screen shows the total, how much I saved or overspent, and where the money went by category. Confirming saves the trip. Every past trip lives in a history list where I can open it up again or delete it, and the home screen turns all of that into a couple of charts and a one-line observation like "you spend the most on meat."

## Dollars and lira

I deal with both US dollars and Lebanese pounds, so the app does too. Each trip has its own currency, and the total is shown in that currency with the other one in smaller text underneath. The exchange rate is something I set myself and can change whenever I need to. Each finished trip remembers the rate it was saved with, so editing the rate later doesn't rewrite my old trips.

## What it's made with

React and Vite for the front end, plain CSS, and Recharts for the charts. The data lives in Supabase (a Postgres database, login and file storage), and the site is hosted on Vercel. Tests use Node's built-in test runner.

## A few notes on how it's built

Screens update straight away and the saving to the database happens in the background, so the app still feels quick on a slow connection in the shop. If a save fails, it reloads what the server has and tells me.

Everything is tied to my account. The database rules only let a signed-in user see their own rows, and the photos sit in a private folder that only I can open. Money is kept as plain numbers and only rounded when it's shown on screen, which avoids the little "$0.01 over budget" surprises that rounding can cause.

I wrote unit tests for the parts where a mistake would cost me the most: the money formatting and conversion, the budget colours and warnings, the trip totals, the chart numbers and the code that talks to the database. The screens themselves I checked by hand.

## Status

It works and I use it. It's a private project, so it isn't open for anyone else to use or contribute to.

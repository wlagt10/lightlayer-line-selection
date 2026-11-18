# lightlayer.net: Premium, Standard or Global? How to Pick the Right Lightlayer Line, Read the Test IPs, and Check the Price Before You Order (Full Plan Table)

Lightlayer sells KVM cloud servers from three data centers: Los Angeles, Taiwan and Manila. Los Angeles offers three network grades (Premium, Standard, Global); Taiwan and Manila each offer Premium and Global. Every plan on its summer sales page is the same 1-core, 1 GB RAM, 50 GB disk instance with one IPv4, billed annually.

The $24.99/year figure that shows up in almost every mention of this host comes from that page: published 10 July 2024, with the event closing on 31 August. It is a two-year-old promotional price, not a current quote. Every number below is the 2024 published figure, and the order page is the only place to confirm what you'll be charged today.

> **Quick answer**
> - Your visitors are mostly in mainland China: Los Angeles **Premium** (CN2 + Mainland BGP + International BGP).
> - You need a bigger port but mainland access still matters: Los Angeles **Standard**.
> - Nobody in mainland China: **Global**, which is also where the cheapest bandwidth per dollar sits.
> - Order page for all of it: 👉 [See Lightlayer's current plans and prices](https://account.lightlayer.net/?affid=74)

## The plans, as published in the 2024 promo

| Plan (all Los Angeles) | Specs | Traffic | 2024 price | Order |
| --- | --- | --- | --- | --- |
| Premium 20M | 1 core / 1 GB / 50 GB / 1 IPv4 | Unmetered | $24.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Premium 30M | 1 core / 1 GB / 50 GB / 1 IPv4 | 1 TB/month | $24.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Standard 50M | 1 core / 1 GB / 50 GB / 1 IPv4 | Unmetered | $24.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Standard 100M | 1 core / 1 GB / 50 GB / 1 IPv4 | 1 TB/month | $24.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Standard 1G | 1 core / 1 GB / 50 GB / 1 IPv4 | 1 TB/month | $83.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Global 100M | 1 core / 1 GB / 50 GB / 1 IPv4 | Unmetered | $24.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Global 200M | 1 core / 1 GB / 50 GB / 1 IPv4 | 1 TB/month | $24.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |
| Global 1G | 1 core / 1 GB / 50 GB / 1 IPv4 | 1 TB/month | $41.99/year | [Check this plan](https://account.lightlayer.net/?affid=74) |

**These are the original figures from a sales page dated 10 July 2024 that ended 31 August 2024. They are not current pricing.** Two rows carry a "1 CORENEW" label in the original table, which reads as a typo for 1 core, since the hardware column is identical everywhere.

All eight rows are Los Angeles. The same page described the Taiwan and Manila lines and gave test IPs for both, but published no plan prices for either location, so nothing here can be quoted as a Taiwan or Manila rate. 👉 [Check what those locations cost now](https://account.lightlayer.net/?affid=74)

One pattern is worth noticing before you pick: at the same $24.99, the unmetered plans get small ports (20M, 50M, 100M) and the metered plans get the big ones (30M, 100M, 200M, 1G). Lightlayer says both traffic models are available across all bandwidths. If you expect steady throughput rather than bursts, the unmetered 20M Premium is a genuinely different product from the metered 30M at the same price.

## Which line do you actually need?

The three Los Angeles grades differ only in routing, and the official definitions are short enough to quote in full.

- **Premium** is CN2 + Mainland BGP + International BGP. Lightlayer calls it the lowest-latency, most stable option for mainland users.
- **Standard** is Mainland BGP + International BGP. It's aimed at people who want larger ports while still keeping mainland latency reasonable.
- **Global** is International BGP only, for users outside mainland China and for US local traffic.

Turn that into a decision:

**Mainland China is your main audience.** Take Premium. You give up port speed (20M or 30M) in exchange for the CN2 path, and that trade is the whole point of the product. A 30M port is enough for a text-and-images site with modest concurrency; it is not enough for video or large downloads.

**You need 50M or more, and China still matters.** Standard. It keeps the mainland BGP component and drops CN2, which is why it can push 100M or 1G at the same or lower price.

**Your users are in Europe, the US, or Southeast Asia.** Global. You're paying for international BGP only, and you should not pay a premium for a China route you'll never use.

The price gap at the top end is the clearest signal in the whole table. Both 1 Gbps plans have identical hardware and 1 TB of monthly traffic, but Standard is $83.99/year and Global is $41.99/year. That's **$42 a year more for the mainland BGP component**, and the sales page doesn't explain the difference. If mainland routing is not on your requirements list, Global 1G is the cheapest gigabit port in the lineup by a wide margin.

👉 [Compare the Premium, Standard and Global plans side by side](https://account.lightlayer.net/?affid=74)

## Test the route yourself before you pay

Lightlayer publishes test IPs for every location and line. This is the most useful thing on the site, because it lets you measure the route from your own network instead of trusting a marketing description.

| Location | Line | Test IP |
| --- | --- | --- |
| Los Angeles | Premium | 38.61.2.254 |
| Los Angeles | Standard | 38.61.5.254 |
| Los Angeles | Global | 38.61.7.254 |
| Taiwan | Premium | 46.8.124.242 |
| Taiwan | Global | 46.8.126.64 |
| Manila | Premium | 154.39.138.254 |
| Manila | Global | 154.39.140.254 |

Ping all three Los Angeles addresses from the place your users actually sit, not from your laptop on a different ISP. Then run a traceroute and look at the path: a Premium route should hand off to CN2 or a mainland backbone fairly early, while Global will wander through international transit. Compare average latency and, more importantly, packet loss over a few minutes rather than a single ping.

Two things can mislead you. ICMP replies are sometimes rate-limited or blocked on individual hops, which makes a healthy route look broken. And a route that is fast from one Chinese ISP can be mediocre from another, so test from more than one network if you can.

Treat Premium as a routing claim rather than a latency guarantee. The CN2 + Mainland BGP combination is a real technical difference, but Lightlayer publishes no latency figures or loss targets to go with it, so your own ping is the only evidence you'll get before paying.

👉 [Ping first, then order the line that wins](https://account.lightlayer.net/?affid=74)

## What's rough around the edges

The site has visible copy problems, and you should factor them into how much you verify before paying.

The homepage contains "Eeasir", "Fexible" and "Windws", and the line "Over Sold over 15000+ host", which is both ungrammatical and a self-reported number with no third-party confirmation behind it. On the Manila section, the Global line is described as being for "local users in Taiwan", an obvious copy-paste from the Taiwan page. The `/website-builder` page is an unreplaced commercial template, complete with a different product name in the title, placeholder body text, and counters reading "0+ Reseller Joined" and "0+ Host has been sold" while the homepage claims 15,000+ hosts. The "0+" figures come from the template, not from Lightlayer's books. None of this says anything about the servers, but it does say the site's localisation and proofreading are thin, so verify anything that matters to you directly.

Three things are not published anywhere on the pages that could be checked:

**Refund window.** No refund period or trial is stated on the official pages. A third-party plan directory lists the policy as provider-fault only, which would mean no change-of-mind refunds. Get this in writing from support before you pay for a year.

**Uptime and SLA.** There is no published uptime percentage or credit schedule. Service credits are the part of a host's terms you only read once, and you want to read them before an outage rather than after.

**Renewal price.** The 2024 sales page said "renew at the same price". That was a statement attached to a promotion that ended in August 2024, not a standing policy, so do not assume it applies to whatever plan you buy now.

Windows deserves its own note: the FAQ says Linux is supported and that Windows is available if you need it, spelled "Windws" on the page. Confirm the version and licensing terms with support for the specific plan, since the FAQ says nothing about cost.

## Other products on the same site

Lightlayer also lists GPU servers built around the NVIDIA RTX 4090 and a Los Angeles dedicated-server line with high-core-count configurations. Those are priced separately from the cloud plans above, and no current figures for them could be confirmed, so this article leaves them alone. If you're shopping for dedicated hardware, price it on the order page rather than assuming the cloud-plan pricing carries over.

## Final selection rules

- **Personal site or small blog, mainland visitors, low concurrency:** Los Angeles Premium 20M unmetered.
- **Site with real traffic that needs headroom and still serves China:** Los Angeles Standard, 100M metered or 1G metered if you need the port.
- **Overseas audience, downloads, mirrors, backups:** Global, and the 1G metered plan is the value pick at the 2024 figures.
- **Taiwan or Manila:** only if physical proximity to those markets is the reason you're buying, since neither location has published plan pricing to compare.

Before you check out, confirm five items on the order page: the price you're actually being charged today, the renewal price and cycle, whether the plan is metered or unmetered and what overage costs on a metered plan, the refund terms, and which payment methods are accepted. If any of those is missing from the page, ask support and keep the reply.

The 2024 numbers above are useful for understanding how the lineup is structured and where the price differences come from. They are not a quote, and the only price that matters is the one on the page when you buy.

👉 [Check Lightlayer's current plans, prices and availability](https://account.lightlayer.net/?affid=74)

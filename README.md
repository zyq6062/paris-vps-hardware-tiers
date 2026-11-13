# Paris VPS: PAR1 or PAR2, What the Hardware Actually Delivers, and Where the Cheap Tier Stops Making Sense

JustHost.asia runs two separate Paris locations, PAR1 and PAR2, and the difference between them is bigger than the difference between most plan tiers you'll compare. A third-party test of PAR1 recorded Geekbench 6 scores of 1272 single-core and 4170 multi-core; the same tester's PAR2 machine scored 786 and 1305. Same brand, same city, roughly three times the multi-core result. If you're buying a Paris VPS here, the location choice comes first and the plan tier second.

Below: what each Paris box actually is, how the network behaves, what the current pricing looks like against other Paris providers, and the support complaints you should read before you pay.

> **Most readers should start with PAR1.** It's the newer AMD EPYC 7762 hardware, it tested at triple the multi-core score of PAR2, and the Chinese carrier return routes were direct in testing. Confirm PAR1 is open for order on your chosen tier before you pay.
> 👉 [Check which Paris locations are open for order right now](https://justhost.asia/?ref=196392)

## The two Paris locations, side by side

Both are KVM virtual machines on NVMe arrays with unlimited traffic, and both include one-click datacenter switching and one-click IP switching. The hardware underneath is not the same.

| Location | Processor (as tested) | Geekbench 6 | Disk I/O | Order |
| --- | --- | --- | --- | --- |
| PAR1 | AMD EPYC 7762 (Zen 2, 64C/128T, 2.0–3.35 GHz) | 1272 / 4170 | ~661 MB/s seq; 4K ~71 MB/s, ~17.8K IOPS | [Order a Paris VPS](https://justhost.asia/?ref=196392) |
| PAR2 | Intel Xeon Gold 6140 (18C/36T, 2.3–3.7 GHz) | 786 / 1305 | ~590 MB/s seq; 4K ~42 MB/s, ~10.5K IOPS | [Order a Paris VPS](https://justhost.asia/?ref=196392) |

Both figures come from independent reviews published in May 2026, not from JustHost's own marketing. The PAR1 machine also showed stronger I/O on the 4K random test, which is the number that predicts how a database or a WordPress install with plugins actually feels. Sequential throughput on both is fine; the gap is in small-block work.

If you're running anything CPU-bound across multiple workers (Node, PHP-FPM pools, a small Postgres instance, a game server), PAR1's multi-core figure is the reason to care. For a single static site or a WireGuard endpoint, either location is more machine than the job needs.

## Where the money actually goes

I'm not printing a monthly figure in this article. JustHost's plan grid, tier names and prices live on the order page, and that grid is the only current source; a number copied into an article is stale the moment the lineup rotates. What I can tell you is the yardstick to judge it against: published prices from other Paris providers, checked in late October 2026.

| Provider | Cheapest Paris Linux tier | 2 GB tier | Notes |
| --- | --- | --- | --- |
| VexCloud | €2.49/mo | — | Equinix PA6, French-language support |
| OliveVPS | $3.99/mo (1 GB, Linux only) | $7.99/mo | Telehouse Paris 2, 7-day refund |
| EDIS Global | €4.99/mo (1 GB) | €8.49/mo | Prices exclude VAT |
| LightNode | $7.71/mo (2 GB) | $7.71/mo | Hourly billing from $0.012 |
| Infrawire | €8.30/mo (4 GB, discounted) | — | Discounted from €16.60 |

Those are other companies' public list prices, not JustHost's. Use them as a range: in this market, a 1 GB Paris VPS sits around €2.50–€5 a month and a 2 GB machine around €7.70–€8.50. If the tier you're looking at lands well above that band, the hardware has to justify it. If it lands below, check what got cut, because something usually did.

Three things to read off the checkout page before you commit:

- **Billing cycle.** Monthly and annual pricing are usually different numbers, and the annual figure is the one that determines your second year.
- **Currency and tax.** Some Paris providers quote ex-VAT, which adds 20% for EU buyers. Whatever the page shows, confirm whether that's the final charge.
- **What switching costs.** One-click datacenter and IP switching is a real feature here, but the terms around it (how often, whether it resets your data) are worth reading rather than assuming.

👉 [Compare JustHost's current Paris pricing against that yardstick](https://justhost.asia/?ref=196392)

## Network: own AS, capped port, unlimited volume

JustHost's French network runs on Baxet, the company's own network, out of Paris. Default port speed is listed at 300–750 Mbps depending on the tier, with unlimited traffic. Read those two facts together: unlimited means no monthly volume cap, and the port speed is where throughput actually tops out. A 300 Mbps port is fine for a website or an API; it's slow for seeding large backups or serving video.

One limitation worth flagging because it's easy to miss: the PAR2 test machine had no IPv6. If your stack depends on IPv6 (mail authentication policies, some CDN and monitoring setups, anything talking to IPv6-only endpoints), confirm the current state of the location you order before you migrate.

Routing to Asia is the other thing to know. The PAR2 test found China Mobile had the best outbound and return paths of the three Chinese carriers, with speeds dropping at peak; China Telecom and China Unicom ran on pure international lines with average results, and the reviewer recommended paid transit for anyone serving mainland users seriously. The PAR1 test found direct return routes on all three carriers without detours, though China Telecom degraded during peak hours.

For European traffic, geography does most of the work. Independent Paris benchmarks from other providers put local latency at 1–3 ms and London around 10 ms, which is the order of magnitude to expect from a well-connected Paris facility. Treat those as market reference points, not as a measurement of JustHost's network.

## The support question, answered honestly

JustHost's Trustpilot page carries a run of negative reviews, and they repeat the same two complaints rather than scattering across a dozen issues. The first is that live chat is bot-only: one reviewer described the bot spending a long stretch denying that an IP belonged to JustHost until a screenshot from the customer account settled it. The second is outages without communication. One review documents a full outage on 2 March 2026 affecting servers and the control panel, with no status page and roughly 15 hours of silence across chat and tickets. Another mentions reinstalls that failed on the first attempt.

Reviews on Trustpilot are self-selected and skew toward people with a grievance, so read them as a signal about failure modes rather than a satisfaction average. The failure mode they describe is specific: when something breaks, you may be waiting a while with no channel that tells you what's happening. If your project has a customer-facing SLA, budget for that risk or keep a standby elsewhere.

For a personal project, a test box, a proxy, or a VPN endpoint, the same characteristic matters much less. That's the honest split.

## Who should buy somewhere else

**You need a formal SLA or a phone number to call.** Nothing in what's verifiable about JustHost suggests enterprise support. Paris providers with documented SLAs and named Tier III facilities exist in this market at €4.99–€8.49 for the entry tiers listed above.

**You need IPv6 on day one.** Confirm it at the location level before ordering, because the tested PAR2 machine didn't have it.

**You only need 1 GB for a static site or a small blog.** Cheaper Paris options exist from €2.49 and $3.99 a month. JustHost's pitch is unlimited traffic, one-click location switching and streaming-friendly IPs, and none of those matter for a five-page site.

**You want a managed panel and hand-holding.** This is unmanaged KVM. You get the box and the reinstall button.

## FAQ

**Which Paris location should I pick?**
PAR1 unless you have a specific reason otherwise. The tested hardware is newer, the multi-core score is roughly three times higher, and the I/O is better on random 4K. Check availability for your tier at checkout, since location availability varies.

**Can I move the VPS or change its IP later?**
Yes. One-click datacenter switching and one-click IP switching are both listed features. If you're switching IPs for reputation reasons, note that these are shared broadcast ranges used for streaming unlocks, so the reputation of the address you land on is not something you control.

**Does the French VPS support IPv6?**
The PAR2 test machine did not. Verify the current status of your chosen location before you build anything that depends on it.

**What payment methods work?**
Cards, PayPal, Alipay, UnionPay and multiple cryptocurrencies, including PerfectMoney on some regional products. If you're paying from outside the EU, crypto or Alipay avoids card FX fees.

**Is it good enough for a paying-customer production site?**
The hardware is. The support model is the open question. For a small business site with tolerant downtime, it's workable; for anything with an uptime commitment attached, either run a second node somewhere else or pick a provider whose support you've already tested.

## How to decide

Running a site or API for French and EU users, and you want the better of the two Paris boxes: choose PAR1, take the smallest tier that covers your RAM needs, and skip the upgrade until memory pressure tells you otherwise.

Serving mainland China from Europe: PAR1 for the direct return routes, and price in transit if Telecom users are a meaningful share of your traffic.

Testing, proxying, or running a VPN endpoint: the entry tier is enough, and the location matters less than the price.

Before you pay, confirm two things on the order page: whether the displayed price includes tax for your billing country, and what the same plan costs on renewal versus your first term. Those two numbers decide whether this is a cheap Paris VPS or an expensive one.

👉 [Start with a Paris plan on JustHost.asia](https://justhost.asia/?ref=196392)

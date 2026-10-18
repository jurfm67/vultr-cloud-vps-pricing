# cloud vps: how to pick a plan you won't outgrow, with Vultr's full pricing and the fine print most pages skip

Search for a cloud vps and you'll land on a dozen landing pages promising the same three things: NVMe storage, a global network, developer-friendly pricing. The spec sheets rarely tell you what actually decides whether a plan works for you: which CPU generation sits behind that vCPU count, whether the cheapest plan can even be reached over a normal IPv4 connection, how generous the included bandwidth really is per dollar, and what kind of support shows up when something breaks at 2 a.m.

Here's the short version. Vultr's shared-CPU Cloud Compute lineup runs from $2.50 to $80 a month, bills hourly with no minimum commit, and spans 32 regions across six continents. For most solo developers and small sites, the sensible entry point is the **$5 plan** (1 vCPU, 1GB RAM, 25GB SSD, 1TB bandwidth) — or the $10 plan once a database moves in. The $2.50 plan is real, but it's IPv6-only, and that single detail disqualifies it for most public websites.

> **Quick picks**
>
> - Personal site or lightweight app: **$5/mo — 1 vCPU, 1GB RAM, 25GB SSD, 1TB bandwidth**
> - Small production app with a database: **$10/mo — 2GB RAM, 55GB SSD, 2TB bandwidth**
> - Need a regular IPv4 address on the cheapest tier? That's the **$3.50** plan, not the $2.50 one
>
> 👉 [See Vultr's current Cloud Compute plans and prices](https://www.vultr.com/products/cloud-compute/?ref=7268283)

## What "cloud VPS" actually gets you

A cloud VPS is a virtual machine with its own operating system and a dedicated share of a physical server's RAM, CPU, and storage. You get root access and can install anything, the provider handles the hardware, and it costs a fraction of renting a whole machine.

The "cloud" part is what separates current offerings from the VPS deals of a decade ago: servers provision through an API in under a minute, billing runs hourly, and you can climb from a $2.50 shared box to dedicated hardware or GPU clusters inside the same account. Shared hosting, by contrast, puts dozens of websites on one machine competing for the same memory and CPU — a neighbor's traffic spike becomes your slow page loads. A dedicated server gives you the entire machine, which is comfortable and usually wasteful unless your workload is consistently busy. A cloud VPS sits between the two: your own reserved slice, none of the hardware maintenance.

## Vultr's Cloud Compute plans: the full current lineup

The table below lists Vultr's Regular Performance Cloud Compute plans exactly as they appear on Vultr's own cloud compute product page. Every plan includes hourly billing with no minimum commit, and every plan except the $2.50 one ships with a dedicated IPv4 address.

| Plan | Storage | Bandwidth | Monthly price | Deploy |
| --- | --- | --- | --- | --- |
| 1 vCPU, 0.5GB | 10GB | 0.5TB | $2.50 (IPv6-only) | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 1 vCPU, 0.5GB | 10GB | 0.5TB | $3.50 (adds IPv4) | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 1 vCPU, 1GB | 25GB | 1TB | $5 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 1 vCPU, 2GB | 55GB | 2TB | $10 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 2 vCPU, 2GB | 65GB | 3TB | $15 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 2 vCPU, 4GB | 80GB | 3TB | $20 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 4 vCPU, 8GB | 160GB | 4TB | $40 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |
| 6 vCPU, 16GB | 320GB | 5TB | $80 | [ Deploy](https://www.vultr.com/products/cloud-compute/?ref=7268283) |

Regular Performance is the budget tier: previous-generation Intel CPUs with regular SSDs. Vultr also lists two faster shared tiers (High Performance and High Frequency) plus four dedicated-CPU families — General Purpose, CPU Optimized, Memory Optimized, and Storage Optimized — and above those, bare metal and GPU plans up to NVIDIA H100 clusters, all under the same dashboard, API, and billing account. Those higher tiers are priced per configuration rather than as a flat ladder, so check them on the same page if the Regular line feels slow for your workload.

### The $2.50 plan is IPv6-only. Read that twice

The $2.50 and $3.50 plans have identical hardware — same vCPU, same RAM, same storage, same bandwidth. The extra dollar buys a standard IPv4 address. Plenty of home and mobile connections still reach servers over IPv4 first, which means an IPv6-only box can be unreachable for a real chunk of your visitors, depending on their network.

So who is the $2.50 plan actually for? Testing environments, internal tools you reach through a tunnel or over an IPv6-capable network, and learning projects where reachability doesn't matter. For anything the public needs to open in a browser, the $3.50 plan is the true floor.

### Bandwidth gets less generous as you climb

Prices roughly double up the ladder; bandwidth doesn't follow the same curve. The $5, $10, and $15 plans all work out to about $5 per TB of included transfer. The $20 plan works out to roughly $6.70 per TB, the $40 plan to $10 per TB, and the $80 plan to $16 per TB.

That's worth knowing if your project moves a lot of data but doesn't need much RAM — at that point, one bigger instance isn't automatically better value on transfer than a smaller one. It also means that if you host anything bandwidth-heavy, you should check each provider's overage rate before committing, since the included TB is a starting allowance rather than an unlimited pipe.

### Same spec sheet, different CPUs

A 2 vCPU plan on a five-year-old Intel Xeon and a 2 vCPU plan on a current-gen AMD EPYC look identical in a pricing table and behave very differently under load. Regular Performance is explicitly the older-Intel tier, and on any shared plan your neighbors on the same physical host affect your consistency.

If you run game servers, latency-sensitive bots, or a database that's actually busy, more RAM won't fix that — the higher-clock shared tiers or the dedicated-CPU families will. Treat the table above as the entry ladder, and the moment your workload feels "slow but the specs look fine," the CPU generation is usually the reason.

## How Vultr compares with DigitalOcean and Cloudzy

At the low end, all three providers are close on price. The real differences show up in region coverage, the upgrade path, and how each one handles support and refunds.

| Provider | Cheapest cloud VPS | Entry storage · bandwidth | Regions | Money-back |
| --- | --- | --- | --- | --- |
| Vultr | $2.50 (IPv6-only); $3.50 with IPv4 | 10GB SSD · 0.5TB | 32 across six continents | — |
| DigitalOcean | $4 (shared CPU) | 25GB NVMe · 1TB (from the $7 Premium tier) | — | — |
| Cloudzy | $2.48 promo (normally $4.95) | 20GB NVMe · 1TB | 13 across four continents | 14 days |

A dash means the provider's own VPS pages don't publish that figure — verify it before buying if a refund window or a specific region matters to you.

DigitalOcean's shared CPU starts at $4, with a Premium line at $7 for 1GB on newer CPUs and NVMe storage. Its dedicated-CPU families start noticeably higher: $42 for a 4GB CPU-Optimized Droplet, $63 for an 8GB General Purpose, $84 for 16GB Memory-Optimized, and $131 for a 16GB Storage-Optimized with 300GB SSD. Cloudzy undercuts everyone on headline price at $2.48 (a 50% promo off $4.95), runs AMD EPYC and DDR5 hardware with NVMe storage, publishes a 99.95% uptime SLA, and offers a 14-day money-back guarantee across 13 regions.

Where Vultr pulls ahead is breadth. Its 32 regions include Johannesburg, Santiago, Tel Aviv, and Warsaw — locations most competitors skip entirely, and a decisive factor if your users are in Africa, South America, or the Middle East. Hourly billing applies across the board, including GPUs and bare metal, so the account you open for a $3.50 box can later deploy an H100 cluster without a new vendor, new API, or new billing setup. Managed Kubernetes, managed databases, block and object storage, and a CDN are native products rather than third-party integrations.

One honesty check: Vultr doesn't win on absolute price. Hetzner undercuts it on raw value, and if cheapest-possible-RAM-per-dollar is your entire decision, that's worth knowing before you commit.

## Where Vultr is the wrong pick

Support on the lower plans is largely self-serve — documentation and community rather than hand-holding chat. Vultr's Trustpilot reviews also surface a recurring complaint about how account suspensions are handled, which deserves attention if your project can't tolerate downtime while a dispute gets sorted. Two practical mitigations: keep current snapshots of anything important, and for genuinely mission-critical production, either buy into a higher support tier or plan redundancy across instances.

A VPS is also the wrong category if you want someone else to administer the server — patching, hardening, tuning. Vultr's managed products are Kubernetes and databases, not full server administration; DigitalOcean markets a managed option through Cloudways for exactly that crowd. If you'd rather never open an SSH session, managed hosting beats a raw cloud VPS regardless of provider.

## Picking a cloud VPS by scenario

- **Personal blog or portfolio, light traffic:** the $3.50 plan with IPv4, or $5 if you want headroom. The $2.50 plan only if IPv6-only reachability genuinely works for you.
- **Dev and staging servers:** hourly billing with no minimum commit makes short-lived boxes cheap. Spin one up per feature branch, destroy it when the branch merges, pay only for the hours it ran.
- **Small production app with Postgres or MySQL:** $10–$20 on the Regular tier gets you comfortably started. Regular-tier storage is standard SSD, though — if disk I/O becomes the bottleneck, that's your trigger to look at the higher storage tiers rather than adding RAM.
- **Users in Johannesburg, São Paulo, Tel Aviv, or similar cities:** region coverage decides this more than spec sheets do. Vultr has 32 regions including the cities most rivals skip; match the provider to where your users actually are.
- **A workload that will need GPUs later:** starting on Vultr means one account, one API, and one bill from the $2.50 shared box all the way to H100 clusters and bare metal.

👉 [Compare Vultr's 32 regions and current plan pricing](https://www.vultr.com/products/cloud-compute/?ref=7268283)

## Cloud VPS FAQ

**Is Vultr's $2.50 plan actually real, or clickbait?**
Real: 1 vCPU, 0.5GB RAM, 10GB SSD, and 0.5TB bandwidth for $2.50 a month. The catch is that it ships without an IPv4 address — the same hardware with IPv4 is the $3.50 plan.

**Does Vultr bill hourly or monthly?**
Hourly, with no minimum commit on standard compute. The prices listed above are what a server costs running for a full month; a server that lives for three days costs a fraction of that. GPUs and bare metal bill hourly too.

**When do I need dedicated CPU instead of shared?**
When your CPU load is sustained rather than bursty — CI/CD runners, video encoding, busy databases — or when consistent latency matters more than the price difference. Shared plans cost less because you split physical cores with neighbors.

**What if I don't want to manage the server myself?**
Then a raw cloud VPS is the wrong product. Look at managed offerings: Vultr provides managed Kubernetes and managed databases, DigitalOcean offers a managed route through Cloudways. A VPS assumes you're comfortable with an SSH session and an update schedule.

## Before you click buy

Two checks worth a minute. First, confirm the region actually helps you — a plan near your users beats a slightly bigger plan far away, and latency is easy to test with a ping before you commit to anything. Second, if your project moves real bandwidth, check the overage rate instead of assuming the included TB is a ceiling you'll never approach.

If you've matched yourself to a tier above, deployment takes about two minutes from checkout to SSH. 👉 [Start on Vultr from $3.50/month with IPv4 included](https://www.vultr.com/products/cloud-compute/?ref=7268283)

---
layout: post
title: "bubblegum & bailing twine"
---

As I write this, Microsoft 365 is limping out of a 20-plus-hour outage. The mechanism, per their own status updates: Exchange servers started failing automated health checks, got pulled from service, and the survivors tipped over under the redistributed load. Traffic never increased. No attack. The trigger, days later, was still "unknown." The health check — the thing whose entire job is preventing cascade — caused the cascade.

That would be forgivable as a one-off. It is not a one-off. Run the tape on 2026:

- Azure took down gateway services across many regions because an *expired deployment restriction* let a giant batch of OS updates run at once. The guardrail had a TTL and nobody noticed it lapsed.
- Cloudflare withdrew eleven hundred BGP prefixes because an automation script read an empty API parameter as "all of them."
- Google's London region went dark when one power feed was in maintenance, the second faulted, and the generators — the machines with exactly one job — failed to start until the batteries ran out. Azure West US did the same dance in February: generators running, transfer control failed, UPS drained anyway.
- Google's Netherlands zone hit 44°C inside because a 3-millisecond voltage dip tripped the breakers and the redundant cooling was unavailable "due to construction."

None of this is exotic. No novel attack, no unprecedented scale problem. This is failover that was never actually tested, change gates that expired silently, input validation that a junior engineer should have caught, and maintenance scheduling that assumed nothing else would ever go wrong. These are the boring disciplines — the ones institutional memory enforces, because somebody in the room remembers 2012 and says "we test the generator transfer under load, every quarter, because of that one night."

Here's my uncomfortable correlation. The industry shed roughly 154,000 jobs in the first half of 2026 alone — more than all of 2025 — with Amazon accounting for half of it and every press release citing AI efficiency. I've run infrastructure organizations for thirty years, and I'll tell you who's expensive on paper: the staff engineer with the gray ponytail and the Birkenstocks who hasn't shipped a feature in years because his job is knowing why the deployment gate exists. He doesn't demo well. His value is invisible right up until the quarter after he's gone — and the planet's shared infrastructure is now running that experiment for us, in production, with everyone's workloads aboard.

Call it what it is: we've crossed the rubicon of malicious incompetence. Not malice of intent — malice of priority. Choosing, repeatedly, with the receipts in hand, to strip the human redundancy out of systems whose entire value proposition is redundancy.

The cloud was never magic. It was other people's computers run by extremely careful people. We're finding out what it costs when only the first half stays true.

Audit your failure modes accordingly. The hyperscaler's SLA credit will not cover your quarter.

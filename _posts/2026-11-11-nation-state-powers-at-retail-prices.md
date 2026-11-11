---
layout: post
title: "nation-state powers at retail prices"
---

There's a use-after-free in the Linux kernel's TCP handshake path — CVE-2026-98432 — that's been sitting in every kernel since 4.4. That's 2016. A race between a retransmitted SYN and a completing handshake, IP options freed on one CPU while another is still reading them. Lose the race and the handshake just fails, so an attacker can retry all day. No credentials. No user interaction. Anything listening on IPv4 TCP on an unpatched kernel, which is a polite way of saying: the internet.

The kernel CNA scored it 9.8. Red Hat's page said 5.9 while their machine-readable advisory said 8.1, Amazon said 7.0 — and as of the end of October, Debian and Oracle had shipped fixes while Ubuntu and RHEL were still "work in progress." A decade-old remote root in the most deployed kernel on earth, and the ecosystem can't even agree on how scared to be, let alone patch on the same week.

But the severity score isn't the story. This is: Anthropic disclosed that their model wrote a working exploit for this bug. Forty-eight minutes to leak a kernel address and defeat KASLR, five more to root. They didn't publish it, and there's no public PoC as I write this. That restraint is nice. It is also temporary, because the capability isn't the artifact — it's the demonstration that kernel exploitation, the discipline that used to separate intelligence agencies from everyone else, now has a going rate measured in tokens.

For most of my 30 years, the hierarchy was stable. Nation-states had exploit developers, patient capital, and time. Criminals bought leftovers. Kids had Metasploit. A reliable kernel UAF exploit — heap grooming, KASLR bypass, the whole liturgy — was months of work by people you could fit in a few conference rooms worldwide. That scarcity was the control. Not the only one, but a load-bearing one.

It's gone. Pandora's box is wide open. A dude with a laptop and an open weighted/open sourced model now sits somewhere on the capability curve that used to require a budget line in a defense ministry. He doesn't have their targeting, their persistence, or their lawyers. He doesn't need them. He needs one listener on an unpatched box, and the patch gap above says he'll have his pick for months.

The people I talk to on the response side are already describing a bad quarter — queues, triage, retainer customers first. Capacity planning in IR assumed exploit scarcity too. Everyone's model of "how many actors can do this" just broke at the same time.

What to do about it hasn't changed, which is almost the depressing part: know what you're running, patch like you mean it, segment like the perimeter is already gone, and watch egress. The fundamentals were always the answer. The difference is the grading curve — the exam is now administered by anyone who wants to take a swing, not just the few who could afford to.

Scarcity was a security control. We just never wrote it down.

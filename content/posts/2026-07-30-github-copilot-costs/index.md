---
title: "GitHub Copilot Costs"
date: 2026-07-30
draft: false
tags: [AI, Software Development]
author: "Antonio Miras"
description: ""
showToc: false
---

In my last post I spoke about how I've been gradually adopting AI-assisted coding. I haven't thought much about costs because the tool had been experimenting major improvements over time and I felt every euro spent had been well deserved. Now, I realize I've gotten to a point where I rely on AI assistants to do my day job, and going back to manual coding would make my productivity take a major hit. Anyway, today I feel the need to check how much and where should I be spending.

 Speaking of finance, as a side note, how can anyone not notice the humongous investments being made by AI companies? Be it datacenters or the crazy valuations of firms yet to turn a profit. That makes you think about how this frenzy is justified from the money side. Don't take me wrong, the LLMs themselves are a marvel and seem like taken from a sci-fi movie, but how are those companies going to make all that money back? Sure, I'm a European developer living in a low-income country. I'll surely be spending a few euros each month on tools, but I don't see coders around here spending in ways that would make the money people in the US happy. Maybe in America things are very different and devs can allocate like $1000/month on AI tools, but I don't plan to increase my spending much and I don't think my employer is either. Furthermore, from the point of view of the regular folks, I don't know of a single person paying for an AI assistant. Truth in Spain we're very frugal so most people get by with on the free tier. This should be made almost non-functional before anyone decides to spend even €10 on software around here.

Anyway, stop rambling. My goal for this post is to summarize how much I'm spending in GitHub Copilot and how I'm using the tool. First, right now I'm on GitHub Copilot Pro+

![copilot-plans](images/copilot-plans.png)

I'm spending $39/month, but my plan, as I've highlighted, has an additional allowance of $70. Of course, a menacing footnote says they're free to remove that kindness whenever they feel like it

![flex-allotments](images/flex-allotments.png)

Let me log in to my Copilot administration page

![copilot-usage](images/copilot-usage.png)

The first thing I notice is that the admin page's measurement unit is the *AI Credit*, not what I'd expect: tokens. We'll elaborate on that later but, for now, if each credit costs $0.01, my monthly budget would be 3900 credits. I'm currently at 4150 but, due to that allowance I noticed later, my monthly budget is 7000 credits. This limit might drop to 3900 at any moment, so when/if that happens I'll start burning through my additional usage, which I've set to another $40. It's also remarkable that the chart starts counting in June 2026. This is because GitHub changed [its billing structure](https://github.blog/news-insights/company-news/github-copilot-is-moving-to-usage-based-billing) recently. They came up with this AI Credit unit and disabled fallback mode when a user burns through their entire budget. I didn't notice anything since the costs remained the same.

Now, what are AI Credits? This is what [GitHub docs](https://docs.github.com/en/copilot/concepts/billing/usage-based-billing-for-individuals#what-are-github-ai-credits) says

>When you use Copilot, the interaction consumes tokens: input tokens (what's sent to the model), output tokens (what the model generates), and cached tokens (context the model reuses or stores). Each token is priced based on the model used.
>
>The cost of an interaction therefore depends on two things:
>
>    1. The model used
>    2. The number of tokens consumed
>
>This total is converted into **AI credits** (1 AI credit = $0.01 USD).

This seems reasonable to me since tokens alone cannot be a good measurement. The same request would take the same amount of tokens for a weaker model, say GPT-5 Mini, as for a state-of-the-art model like Claude Opus 5.




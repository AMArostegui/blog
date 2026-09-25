---
title: "My backup system and possible improvements"
date: 2026-09-23
draft: true
tags: [Computing, General]
author: "Antonio Miras"
description: ""
showToc: false
---

# How do most people store their data?

I often wonder how regular (non-computer) people keep their backups organized. Never mind being tech-savvy or not, I'd think everyone keeping their information in the digital world has a strategy in case things go wrong, their cell phone is stolen, computers break down, cloud account access is lost, or any other setback.

I think most people, 90%? keep their data using the big american tech conglomerates premises. iPhone/Mac users will store everything in Apple Cloud and Windows and Android users in OneDrive / Google Drive. But how many space do those providers grant for free? This is what ChatGPT has to say as of Sept 2026

| Ecosystem | Free cloud storage | Shared with |
| --- | --- | --- |
| Apple / iCloud | 5 GB | iPhone/iPad backups, iCloud Photos, iCloud Drive, Mail, etc. |
| Google / Google Drive | 15 GB | Google Drive, Gmail, and Google Photos |
| Microsoft / OneDrive | 5 GB | OneDrive files/photos, Outlook.com attachments, and Microsoft 365 app data |

> The notable exception is email: Microsoft also gives 15 GB of separate Outlook.com mailbox storage, while OneDrive’s 5 GB is the cloud-file quota.
> Although Android does not inherently require Google Drive—manufacturers and users can choose alternatives. In practice, Google’s 15 GB is the most generous of the three default bundles, but it fills with mail and photos as well as files.

I think those are fairly generous free allowances, but not enough for the regular folk that spends his holidays shooting pictures. Let's see what paying a fee takes you. These are Spanish prices:

| Provider | Paid storage tiers | Typical monthly price |
| --- | --- | --- |
| Apple iCloud+ | 50 GB · 200 GB · 2 TB · 6 TB · 12 TB | €0.99 · €2.99 · €9.99 · €29.99 · €59.99 |
| Google One | 100 GB · 200 GB | €1.99 · €2.99 |
| Microsoft / OneDrive | 100 GB · 1 TB · up to 6 TB family | €2 · €10 · €13 |

> A few practical distinctions:
> - Apple: storage is for one Apple ecosystem; the 200 GB plan and up can be shared with family.
> - Google: the quota covers Gmail, Drive, and Photos, and can be shared with up to five other people. Google also now sells larger AI bundles: 400 GB (AI Plus), 5 TB (AI Pro), and 20–30 TB (AI Ultra), but these are primarily AI subscriptions rather than straightforward storage upgrades.
> - Microsoft: 100 GB is Microsoft 365 Basic. The 1 TB Personal plan (€99/year) includes Office apps; the €13/month Family plan is six separate 1 TB allocations, not one pooled 6 TB bucket.

To me, all are good value for money, but I don't want to keep my personal data on foreign companies' servers, not just for privacy concerns (in the end, I'm a Windows user; you have to give something), but for the conflict of interests between a private wealthy foreign company and me. Maybe tomorrow an AI bot, trained to keep the interests of the company's lawyers and some department of the US state, would automatically flag my account as problematic. Who, then, am I going to complain to? These companies are famous for their lack of customer service, and for them, I'm a drop in the ocean, so they'd better remove my account than risk me being a terrorist or a non-law-abiding citizen. Although some people have proven it's possible to move things on Hacker News or Reddit and get the attention of an employee in a high enough position, this remains very unlikely.

I decided a long time ago that I wouldn't rely on any cloud or storage providers to keep my data, although I'm making my life more difficult. People choose the easy out-of-the-box solution because they are willing to trade privacy for convenience, knowingly or not. And about ther safety concern, that I hinted at in the above paragraph, honestly, how often have you heard about an Apple/Google/MS account being frozen, compared to people who lost their data after an external disk or a computer broke down. For your average non-computer guy, the safest option is to go with one of the major providers.

I need to implement a reasonable level of security while a keeping the effort to handle my backups low.

# What do I need? Categorizing the data I need to backup

I sort my data using a double hierarchy, according to privacy *Offline, Online* or *Public* and frequency of access *Hot, Cool* or *Cold*. Each file is sorted into one category for each hierarchy.

According to privacy, *Offline* data cannot be accessed through the internet. However, it would be acceptable to keep files in this category behind a VPN, only if it is managed by me. This category includes my house deed, banking information, SSH certificates, or passwords I don't keep in the manager. *Online* information is still private, only for my eyes, but unauthorized access wouldn't be the end of the world. It includes things like my pictures collection or private code repositories. I have very little *Public* information. It's limited to open source projects I keep on GitHub, and this blog.

Access frequency is, as expected, related to how new the information is. Everybody accesses newer information more often, but sometimes, a file can be quite old but still frequently accessed because it keeps a whole history, or simply, the older information is replaced by newer information. My pictures collection is *Cool Data*, my house deed is *Cold Data*. This blog, the repositories of active projects, and my national ID card are *Hot Data*.

![data-classification-map](images/data-classification-map.svg)

# My current setup

Three pieces of hardware are involved in my current setup








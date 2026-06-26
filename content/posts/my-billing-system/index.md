---
title: "My Scrappy Hourly Billing Setup for Dev Work"
date: 2026-06-20
draft: false
tags: [General, Systems]
author: "Antonio Miras"
description: ""
showToc: false
---

As many other developers, I keep a side-gig apart from my day-job.

I got first contacted by a colleague who asked whether I'd be willing to build a computer program together and become partners. I'd do all the coding and would bill him by the hour and get a fee for each deployment. He'd bring all the business logic, and the ability to get the money from the customer after you get the job done. This is not a given in Spain.

I was wondering not just how to keep an honest track of the worked hours, but how to clearly inform my partner of my progress. Although he's also a computer scientist, life lead him to the industrial sector. He's built real-world software used by actual customers; he's crafty and knowledgeable but not really aware of the latests tools and trends of the software world.

# Hourly tracking

To track the worked hours, I thought I could use an on-line calendar I'm a heavy user of anyway. Long ago, I started with Google Calendar but after a phase trying to de-Google my life (I'll talk about that in another post) I explored a few alternatives and end up choosing FastMail.

![Fastmail](images/fastmail.png)

They advertise themselves as *email and calendar made better* and that's what I've found. For a very reasonable price (60€/year) I keep my emails (using my own domain), on-line calendars,   contact list, and 10 GB of online storage space to use as I please.

Back to the point. Now that I have an on-line calendar provider, using an standard protocol (CalDAV/iCal) I can use its entries or appointments to keep track of the worked hours.

I keep a specific calendar for each customer, separate from others intended for personal usage.

![Calendars](images/calendars.png)

# Activity description

I need to keep a good description of each entry I place in my calendar. The the information I'm sending my partner each month is extracted from each calendar entry; time elapsed and description.

Anyway, I felt like for some entries, those taking several hours, having just a description might not be enough information.

Why not sending the commit log from Git alongside each calendar entry? This will be overkill for most entries, but handy for some others. And, despite the relation with my partner being quite good, is good for my peace of mind.

# Putting everything together











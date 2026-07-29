---
title: "My experience using LLMs as a software developer"
date: 2026-07-23
draft: true
tags: [LLM, AI, Software Development]
author: "Antonio Miras"
description: ""
showToc: false
---

# My AI assisted coding history 

It seems ages have passed by, but it was only 2020 when ChatGPT-3 was released. We developers and technology enthusiasts had been aware, but in November 2022 ChatGPT-3.5 was released to the mass market and rocked the world. This is the timeline

![chatgpt-timeline](images/chatgpt-timeline.png)

At first I used the thing as many other developers, I assume. Just copy and paste from the browser or ChatGPT app to the IDE. This was fine for scripts or very localized problems and that small assistance on my daily coding would be enough for a couple of years until I subscribed to GitHub Copilot in August 2025.

As I write, I'm checking the release dates of the main AI coding assistants. I'm surprised to learn GitHub Copilot was among the first in October 2021, earlier than Cursor and Windsurf, both released in 2023. But I didn't know OpenAI themselves were behind GitHub Copilot, so now things make sense.

But back to my use case. Since I subscribed to Copilot, I've been gradually increasing its usage. For the first 7 months the $10 tier (Copilot Pro) was enough for me; I rarely ran out of tokens. For the most part I kept doing manual coding and I usually selected the free models for basic syntax assistance and switched to paid models only when required. But in February of this year I changed to Copilot Pro+ because I had stopped using free models and despite still coding, the AI was becoming so good I kept coming back to the agent more and more.

It has now reached an ability level such that, for developing a prototype from scratch, manual coding is a waste of time. However, for production environments with large and complex codebases things get trickier. On one hand, assuming a localized problem in a single source code file, the agents are also wiser but, more importantly, make far fewer errors than a lowly human developer. On the other hand, the thing is **unable to keep all the context of such big codebases, and navigating many files takes a long time and consumes many tokens**.

The obvious approach is using manual references to tell the agent which files to consider

![manual-references.png](images/manual-references.png)

But it would be great if the agent knew how to navigate the codebase without me constantly assisting it. Furthermore, after recent updates in Copilot pricing and the stock exchange frenzy, token cost is increasing by the day.

My next step in AI coding is to sort these problems out.

# Next steps in AI coding

Before I start, a prerequisite. For my private project repositories the remote is a Linux box I have at home. I keep some projects hosted on GitHub but many aren't, so the idea is, despite using Copilot, to ignore GitHub-only features to avoid lock-in. So features as shown in this page [Copilot on GitHub](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/configure-access-to-ai-models) Ideally all AI enhancements should be as portable as possible. At day-job my employer has provided the developers with ChatGPT Codex accounts, so I can compare both systems to see whether things work on both.

## Persistent codebase instructions

The information shown in [GitHub Copilot in your IDE](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions-in-your-ide/add-repository-instructions-in-your-ide) supports well-known IDEs: VS Code, Visual Studio, JetBrains, Eclipse and Xcode. I think any IDE would work, so that's a good starting point.

We can define a `.github/copilot-instructions.md` file to write repository-wide instructions. This is a copilot-only feature. We can also create `AGENTS.md` files to define instructions in a given folder or the directory root. This latter feature is an [open documented standard](https://github.com/agentsmd/agents.md) adopted by all major players, so I'm going with this.

According to the docs, in Visual Studio Code we can check that our instructions have been considered by looking at the references the agent shows after responding.

> The instructions in the file(s) are available for use by Copilot as soon as you save the file(s). Instructions are automatically added to requests that you submit to Copilot.
>
> Custom instructions are not visible in the Chat view or inline chat, but you can verify that they are being used by Copilot by looking at the References list of a response in the Chat view. If custom instructions were added to the prompt that was sent to the model, the .github/copilot-instructions.md file is listed as a reference. You can click the reference to open the file.

I have a trading bot repository that has never made any money. At least it's going to be useful for testing AI features and, hopefully, for being my first agent-first personal project.

Let's create my first top-level `AGENTS.md` file

![first-agent-md-file.png](images/first-agent-md-file.png)

Pretty straightforward. I just state the purpose of the repository and give simple navigation hints.

Let's ask the agent what this repo is about, and check whether it queried the file. Obviously, I won't give a manual reference to check whether it automatically grabs information from the file

![successfully-referenced](images/successfully-referenced.png)

Fine, it got the memo. Now I can keep writing AGENTS.md files in each folder, giving granular information for each module.

## Tools and Skills

AGENTS.md create persistent context for AI agents; we're just giving more information to our agent. Now, in order to increase its usefullness, we need dynamic features.

We've been using AI tools from the beggining without much tought. Indeed for coding an LLM alone is barely enough, simple tools like searching files, reading its contents or browsing the web are required. Thankfully most AI agents bring those out of the box, [these are VS Code builtin chat tools provides](https://code.visualstudio.com/docs/chat/chat-tools)

[vscode-ai-chat-bultin-tools](images/vscode-ai-chat-bultin-tools.png)

Now tools, as their name suggest, are straightforward abilities; actions our agent can invoke, but to increase knoledge we use a different abstraction called skills. Plenty of web articles like [this](https://www.youtube.com/watch?v=swt76LCfZv4&t=280) are available explaining the difference.

Is relevant that agent skills are also an [open standard](https://agentskills.io/home)

## Codebase navigation

Graphify is the code navigation skill introduced at work, so this is the one I'm going to evaluate. The docs state 

> No account, no API keys, nothing leaves your machine

so it nicely fits my lock-in requirements and also [supports all relevant AI coding assistants](https://graphify.com/integrations)

This is a python tool. I didn't want to polute the virtualenv my trading bot uses, so I had to create a separate one. Use your favorite Python venv/package tool, I'm still in venv/pip

![install-graphify](images/install-graphify.png)

Now we have the command line tool available. Next step is to execute the tool to install the skill and make it available for the assistant

![install-graphify-skill](images/install-graphify-skill.png)

As the skill is now installed I should have the ability to talk about it to my agent. I had first to enable the right virtualenv in the hidden terminal the agent uses

![activate-graphify-virtualenv](images/activate-graphify-virtualenv.png)

but after that, I asked to build the code graph scoped to the folders I wanted and, after a while, did it nicely

![graphify-graph-created](images/graphify-graph-created.png)

The tool provides a nice HTML representation of the graph. It might not be that useful but at least I can use it to check the information graphify mapped is correct 

![html-graph](images/html-graph.png)

It looks good to me. Dangling nodes are `__init__.py` files. Now we can use the skill to ask questions

![first-graphify-navigation](images/first-graphify-navigation.png)

It'll take a while to assess how useful the skill is. On a bigger source code base (at day job) I'll get a more informed opinion.

















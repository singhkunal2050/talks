---
theme: default
background: https://images.unsplash.com/photo-1557683316-973673baf926
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Building a Blog Publisher MCP
  Using Cursor to build and publish blogs right from your IDE
drawings:
  persist: false
transition: slide-left
title: Building a Blog Publisher MCP
mdc: true
---

# Building a Blog Publisher MCP

Using Cursor and publishing blogs right from cursor

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: center
---

# Problem

<v-clicks>

- Hello Everyone, I am **Kunal**, Staff Engineer at Clevertap
- Apart from code, I enjoy writing, playing football and Cats 🐱

</v-clicks>

---

# Writing has always been something I enjoy

<v-clicks>

- Small or big
- At work or for personal learnings
- I always enjoyed sharing knowledge through writing

</v-clicks>

---

# The Challenge

<v-clicks>

- Everyone wants to write
- But tools and maintenance overhead seems huge
- The friction stops us from writing more

</v-clicks>

---

# My Blog Setup

<v-clicks>

- I maintain a blog at **singhkunal2050.dev/blogs**
- Write about anything I find interesting
- Initially used a CMS Editor

</v-clicks>

---

# The Problem with AI Era

<v-clicks>

- I brainstorm ideas using AI Assistants
- Finalize drafts with AI help
- Then had to copy-paste into CMS
- Edit again in the CMS... **Cumbersome!**

</v-clicks>

---
layout: center
---

# 💡 The Idea

<v-clicks>

**Why can't I publish my blog without leaving my AI Assistant?**

- Could be Cursor, Claude, or any AI Assistant
- Conversationally publish blogs
- Sounds cool, right?

</v-clicks>

---

# Building It with Cursor

<v-clicks>

- No prior knowledge of MCP Architecture
- Cursor came to the rescue
- Within **just an hour** - working MCP Server!
- (with some minor hiccups)

</v-clicks>

---
layout: center
---

# What are MCPs?

---

# Model Context Protocol (MCP)

<v-clicks>

- A protocol like HTTP or FTP
- Helps 2 systems talk to each other
- AI Applications ↔ External systems, data sources, tools

</v-clicks>

---

# The USB-C Analogy

> "Think of MCP like a **USB-C port** for AI applications. Just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems."

<div class="pt-4">
  <em>— MCP Documentation</em>
</div>

---
layout: center
---

<img src="/mcp-simple-diagram.avif" class="h-100 mx-auto" />

---
layout: center
---

# Our Architecture

---
layout: center
---

<img src="/architecture.png" class="h-100 mx-auto" />

---
layout: center
---

# The Flow

<div class="text-xl leading-relaxed">

**AI Assistant** ↔ **BlogPublisher MCP Server** ↔ **Tools with schema** ↔ **GitHub utils** → **Blog Published** ✨

</div>

---
layout: center
---

# Let's Go Over the Code

*Fold all code in index.ts and showcase the high-level flow*

---
layout: center
---

# Flow Example: List Blogs

*Walk through one flow end-to-end*

---
layout: center
---

# Demo Time! 

Let's add a new feature using Cursor

**Adding `get_blog_post` - Read a specific post**

```text
Can you check my blogs to find the jamstack 
and show its details
```

---
layout: center
---

# Connecting MCP Server to Your Agent

Two approaches:

<v-clicks>

1. **Local MCP Server** (What we're using today)
2. **Remote MCP Server** (Try this at home!)

</v-clicks>

---

# Local Setup - Cursor

**Steps:**
1. Open Cursor Settings
2. Go to MCP Servers
3. Click "New MCP Server"
4. Add your server config in JSON

---

# Local Configuration Example

```json {all|2-3|4-5|6-10|all}
{
  "mcpServers": {
    "blog-publisher": {
      "command": "/path/to/node",
      "args": ["/path/to/dist/index.js"],
      "env": {
        "GITHUB_TOKEN": "your-token",
        "REPO_OWNER": "singhkunal2050",
        "REPO_NAME": "singhkunal2050v2"
      }
    }
  }
}
```

<v-click>

💡 You can add as many servers as you want!

</v-click>

---

# Remote MCP Server

<v-clicks>

- Host your MCP server online (Render, Railway, VPS, etc.)
- Get the public URL
- Add it to Cursor MCP Servers settings

</v-clicks>

---

# Remote Configuration Example

```json {all|4|all}
{
  "mcpServers": {
    "blog-publisher": {
      "url": "https://your-remote-mcp-server.com",
      "env": {
        "GITHUB_TOKEN": "your-token",
        "REPO_OWNER": "singhkunal2050",
        "REPO_NAME": "singhkunal2050v2"
      }
    }
  }
}
```

<v-click>

**That's it!** No need to run anything locally 🚀

</v-click>

---

# Claude Desktop Integration

<v-clicks>

Works exactly the same way!

**Quick steps:**
1. Open Claude Desktop settings
2. Add your MCP server URL + credentials
3. Save—done!

</v-clicks>

---

# Claude Desktop Config

```json
{
  "mcpServers": {
    "blog-publisher": {
      "url": "https://your-remote-mcp-server.com",
      "env": {
        "GITHUB_TOKEN": "your-token",
        "REPO_OWNER": "singhkunal2050",
        "REPO_NAME": "singhkunal2050v2"
      }
    }
  }
}
```

<v-click>

Your custom tool is now ready in Claude! 🎉

</v-click>

---
layout: center
---

# Live Demo

Let me publish a Cursor Meetup blog post from Mumbai

---
layout: center
---

# The Bigger Picture

---

# Endless Possibilities

This is just **one example** of workflows that felt impossible pre-MCPs

<v-click>

<img src="/possibilities.png" class="h-80 mx-auto mt-4" />

</v-click>

---
layout: center
---

# Connect Anything

<div class="text-xl leading-relaxed">

Connect and create workflows with **any third party**

Talk to it in **natural language**

Using **any AI Assistant** that supports MCP

</div>

---

# Learn More

<v-clicks>

- 📚 [MCP Documentation](https://modelcontextprotocol.io)
- 🌟 [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers)
- 💻 Check out MCP servers from top companies

</v-clicks>

---
layout: center
class: text-center
---

# Thank You!

Questions?

<div class="pt-4 text-xl">
  <carbon:logo-github class="inline"/> singhkunal2050
</div>


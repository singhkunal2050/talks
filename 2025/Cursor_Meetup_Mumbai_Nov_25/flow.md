### Building a Blog Publisher MCP using Cursor and publishing blogs right from cursor


### Problem

Hello Everyone, I am Kunal, Staff Engineer at Clevertap, Apart from code, I enjoy writing, playing football and Cats

---

Writing has always been something that I enjoy, small or big, at work or for my personal learnings and sharing, I always enjoyed writing

---

The problem with writing is that all of us want to write but the tools and the maintainance overhead often seems huge

---

I maintain a blog at singhkunal2050.dev/blogs where I write anything and everything that I find interesting, I used to write usign the CMS Editor that I have setup for my blog.

---

After the advent of AI though I found myself brainstoring ideas and finalizing my draft using my AI Assistants and it felt cumbersome to paste the results back into the CMS and edit them

---

I thought why cant I publish my blog without leaving my AI Assistant, it can be Cursor, Claude or any other AI Assitant
But having the power of just converstionally publish my blogs sounded so cool

---

I did not have any clue about using MCP Architecture and creating MCP servers, but Cursor came to the rescue, Within just an hour I was able to build the MCP Server with some minor hicups

---

What are MCPS?

MCPS(Model Context Protocol) is a Protocol just like HTTP or FTP or any other protocol that helps 2 systems talk to each other, In our case our AI Application can talk to any external system, data source, tool etc.

As per MCP Docs
> "Think of MCP like a USB-C port for AI applications. Just as USB-C provides a standardized way to connect electronic devices, MCP provides a standardized way to connect AI applications to external systems."

![MCP](./mcp-simple-diagram.avif)

---
Now that we understand what MCPS are we can go over ours
Here is how the architecture looks like

![Architecture Diagram](./architecture.png)


---

AI Assistant <-> BlogPublisher MCP Server <-> Has tools with schema <-> Calls github utils to publish a commit to repo -> Blog Published 

---

Lets go over the code 

Here fold all the code in index.ts andshow case the high level flow 

--- 

explain them one flow e2e (list blogs)

--- 

Add one flow using cursor code(get_blog_post - Read a specific post)
 - best case the live demo works
 - the single post data is shown 
 - worst case the `demo` branch is used to show the new tool

```
Can you check my blogs to find the jamstack and show its details
```

--- 

Now that we have undertood how to build the MCP Server
lets understand how we can connect it to our agent 

- Local MCP Server (What we are using)
- Remote MCP Server (What you can try at home)


--- 

- local

For Cursor > Open Cursor Settings > MCP Servers > 
New MCP Server > Will open json file > add your mcp server configs 

like so

```json
{
  "mcpServers": {
    "blog-publisher": {
      "command": "/Users/kunal.singh/.nvm/versions/node/v18.20.4/bin/node",
      "args": [
        "/Users/kunal.singh/Dev/poc/blogPublisherMCP/dist/index.js"
      ],
      "env": {
        "GITHUB_TOKEN": "---",
        "REPO_OWNER": "singhkunal2050",
        "REPO_NAME": "singhkunal2050v2"
      }
    }
  }
}

```

You can add as many servers as you want 
---

- remote

For Remote MCP Server > Host your MCP server online (Render, Railway, VPS, etc.)
> Get the public URL > Add it to Cursor MCP Servers settings

Example config:

```json
{
  "mcpServers": {
    "blog-publisher": {
      "url": "https://your-remote-mcp-server.com",
      "env": {
        "GITHUB_TOKEN": "---",
        "REPO_OWNER": "singhkunal2050",
        "REPO_NAME": "singhkunal2050v2"
      }
    }
  }
}
```

That’s it—no need to run anything locally, just connect to the hosted URL!


---
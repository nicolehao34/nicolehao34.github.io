---
layout: post
title: Software engineering basics they don't teach you at school
---

# OAuth (Open Authrotization)

## What it is
OAuth (Open Authorization) is an open standard protocol that lets an application access resources (like data or services) on behalf of a user, without the user having to share their password.

Think of it as a way of saying:
"Hey, I give this app permission to do certain things for me, but it doesn’t get full access to my account or my password."

## 📱 Everyday Example

When you log into a website using your Google, Facebook, or GitHub account, that’s OAuth in action.

You click "Log in with Google".

The website redirects you to Google, which asks: "Do you want to let this app see your email and profile info?"

You say yes.

Google sends back a token (a special key) to the website.

The website can now use that token to get your info (like your name and email), but it never sees your Google password.

## 🧩 Key Concepts

- Resource Owner → You (the user)

- Client → The app that wants access (e.g., Spotify)

- Resource Server → The API holding the data (e.g., Google’s servers)

- Authorization Server → Issues tokens (e.g., Google Auth server)

- Access Token → A short-lived key that the app uses instead of your password

## 🔗 Why OAuth matters when setting up an MCP server

When you set up an MCP server for, for example,  Jira and Confluence, your server (the “client”) needs a secure way to talk to Atlassian’s APIs on behalf of a user (or sometimes a service account).

Jira and Confluence data (issues, projects, pages, etc.) live inside Atlassian Cloud.

Atlassian requires authenticated API calls (you can’t just hit their endpoints raw).

Instead of storing your username + password in the MCP server (which is insecure and often disabled in Atlassian Cloud), you use OAuth.

## 🛠️ What OAuth gives your MCP server

- Authentication & Authorization – Proves who the MCP server is acting for.

    - Example: “This MCP tool is allowed to create Jira tickets for Nicole’s account.”

- Scoped access – Only the permissions you request.

    - Example: The tool may only need "write:jira-work" and "read:confluence-content", not full admin access.

- Token-based access – MCP gets an access token from Atlassian. 

    - It uses that token to call Jira/Confluence REST APIs. When the token expires, MCP can use a refresh token to get a new one.

## ⚙️ How OAuth Works (Simplified Flow)

- Authorization request – The app asks for your permission.

- User consent – You log in to the provider (e.g., Google) and approve.

- Token exchange – The app gets an access token.

- API access – The app uses the token to request your data from the resource server.

- Refresh tokens (optional) – Let the app request a new access token when the old one expires.

## 📦 How it fits into MCP

MCP Tool (e.g., MCPJIRACreateIssueTool) → Needs credentials to talk to Jira.

Instead of passwords or API tokens, you configure OAuth:

- Register your MCP server as an OAuth client in Atlassian Developer Console.

- Get a Client ID and Client Secret.

- Set redirect URLs for your MCP server.

- When first run, MCP does the OAuth handshake (browser redirect to Atlassian → user consents → Atlassian returns token).

After that, MCP just uses the access token to make API calls (like creating issues or fetching Confluence pages).


Basically, Your MCP server is the “client.”

Atlassian is the “resource server.”

You set up OAuth so your tool can call Atlassian’s APIs securely.
✅ This lets your tool create issues, read pages, etc. in Jira/Confluence.

## Accessing MCP itself

This is different. If you want an external tool (or even another MCP client) to talk to the MCP server, that’s not OAuth with Atlassian. That’s about:

How your MCP server exposes endpoints.

What kind of authentication (if any) you wrap around the MCP itself.

By default:

MCP uses FastMCP / WebSocket transport (ws://localhost:9001) for clients like your tools.

You don’t normally need OAuth inside MCP itself unless you want to secure access between multiple users/clients.

Think of it like this:

MCP server = middleman (broker).

MCP tools = plugins that know how to talk to external systems.

If you want your “tool” to talk to MCP → it just calls MCP methods via the MCP client (fastmcp.Client or ArtianClient). No OAuth needed here unless you’re hardening MCP itself.


# MCP (Model Context Protocol)

## How to Connect your tool/agent to MCP?


# DNS

# Webhook

# Microservices

# FTP

# SSE

# Image

# Nginx

# Subnet Mask

# Node

# http

# WebSocket

# Redis

# Cache

# Virtual Machine

# Port

# Cloud Development

# SDK

# json

# CDN

# Session 

# jwt

# Token

# SQL

# Docker

# Kafka

# API

# Cookie
# OAuth
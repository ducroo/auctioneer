# auctioneer

auctioneer is an AI agent for amateurs who need to post, monitor, and clear a large number of second-hand items on online marketplaces in Switzerland.

Typical use cases include moving house, handling an inheritance, clearing a storage room, or helping a charity Brockenhaus process many individual items. The project is designed for people who are not professional resellers, but who suddenly need a reliable way to turn many physical objects into well-described listings, buyer communication, and completed handovers.

auctioneer works with many agent harnesses, such as OpenClaw, Codex, Claude Code, and similar skill- or workspace-based agent environments. The project is currently light on Python code. Its main focus is building a stable, auditable process around agent skills, local item folders, marketplace-specific rules, and approval gates.

## Goals

- Turn photos and rough notes into structured item records.
- Draft marketplace listings in Swiss-style German.
- Help choose prices, platforms, delivery options, and posting strategy.
- Post and track listings on Swiss marketplaces such as Ricardo, tutti, and others.
- Monitor buyer questions, sales, stale listings, and follow-up tasks.
- Coordinate payment, pickup, shipping, and physical clearing.
- Keep sensitive data local and out of the repository.

## Process

auctioneer is organized around three parts.

### 1. Posting

Posting turns an object into a live marketplace listing.

Relevant skills:

- `item-ingestion`: creates an item folder, extracts visible facts from photos and notes, identifies missing information, and drafts listing material.
- `sales-strategy`: recommends marketplace, price, sale format, packaging, and delivery strategy.
- `marketplace-posting`: prepares the final posting packet, stages photos, checks approval state, and guides form entry.
- `ricardo-browser-assist`: handles Ricardo-specific browser rules, persistent profile use, Cloudflare boundaries, and reusable form knowledge.
- `agent-browser`: optional browser automation support for deterministic form work in already trusted sessions.

For Ricardo, the workflow uses a local `ricardo-posting.md` packet and staged upload photos before opening the browser. The goal is to make browser work mechanical: choose category, fill known fields, upload photos, review, and publish only after explicit approval.

### 2. Monitoring

Monitoring keeps track of active listings and incoming communication.

Relevant skills:

- `gmail-mailbox`: reads and normalizes auction-related email notifications, including Ricardo alerts.
- `buyer-qa`: prepares buyer-question replies and keeps replies approval-gated.
- `daily-report`: summarizes item status, Q&A queues, sales, pickups, shipping tasks, and stale listings.
- `auction-operations`: coordinates the overall lifecycle across item folders, listings, buyer messages, and reports.

Monitoring is meant to answer questions such as:

- Which listings are active?
- Which buyer questions need an answer?
- Which items sold?
- Which listings are stale?
- Which tasks need a human to approve something?

### 3. Clearing and Physical Pickup

Clearing turns a sale into a completed handover and, ultimately, an emptier room.

This part covers:

- agreeing on pickup times
- checking availability against a local calendar
- tracking payment state
- tracking whether an item has been picked up, shipped, or still occupies space
- preparing buyer messages for pickup or shipping coordination
- keeping full addresses and private contact details out of public listings

This workflow is currently less formalized than posting, but it is part of the intended auctioneer lifecycle.

## Safety and Privacy

This repository contains the workflow and skills, not private operational data.

The following should stay local and should not be committed:

- marketplace account credentials
- browser profiles
- buyer messages
- personal memory files
- email inbox data
- OAuth tokens or secrets
- live auction item folders with private photos or logistics
- full pickup addresses

Publishing, editing live listings, sending buyer replies, changing prices, and similar external actions should remain approval-gated.

## Current State

auctioneer is an early open-source tool for others, but it is still process-first rather than app-first. The repository currently focuses on skills, templates, and operating rules. More Python automation may be added once the workflow is stable.

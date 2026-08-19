# Approval workflows & notifications

By default a proposed link waits for a person to approve it. The right approver is usually the
owner of the domain the link would be written into, not whoever is logged into Kenaptic, and
that owner has to know something is waiting.

An **approval workflow** belongs to a domain. It gives that domain's owners two functions in an
external tool:

- **Decisions** — approve or reject a proposed cross-link from Slack, a webhook-connected tool,
  or email, without a Kenaptic login.
- **Notifications** — short messages when something on that domain needs attention, with a link
  to the relevant page.

Both use the same destination, configured once per domain.

## Safety model

A decision can only accept or reject a link Kenaptic has already proposed between two pages of
your own estate. No message, callback or emailed link can introduce a URL of its own, change
what a link says, or modify a page. Approved links still wait for an administrator to deploy
them; nothing publishes from a chat click alone.

Each workflow carries a list of **approvers**, named in advance by an administrator on the
domain record. A click from anyone not on that list is rejected and changes nothing. Because
the approver list establishes identity, approvers never see a login form.

## Setup

The last step of the add-domain wizard offers the approval workflow. You can skip it and add
one later from the domain's record, or remove one at any time. Neither affects the domain's
crawling or cross-link publishing.

For an existing domain: **Domains → open the domain → Approval workflow**.

1. Pick the tool: **Slack**, **Discord**, **Webhook** (any tool that accepts one), or **Email**.
2. Fill in the fields for that tool. The form asks only for values Kenaptic cannot derive:

   | Tool | You provide |
   |---|---|
   | **Slack** (push) | The channel's incoming webhook URL and your Slack app's signing secret |
   | **Slack** (pull) | A bot token and the channel ID — for networks where Slack can't call in; approvers decide with ✅ / ❌ reactions |
   | **Discord** (push) | A bot token, the channel ID, and your app's public key — approvers decide with buttons |
   | **Discord** (pull) | A bot token and the channel ID; approvers decide with ✅ / ❌ reactions |
   | **Webhook** | The URL Kenaptic posts to and a shared secret |
   | **Email** | Nothing — the mail goes to the approvers you name |

   For Discord push, set the app's *Interactions Endpoint URL* to the address shown on the
   form; Kenaptic answers Discord's validation handshake automatically. Approvers are Discord
   user IDs. Microsoft Teams is reachable through the **Webhook** tool via a Power Automate
   Workflows flow (Office 365 connectors are retired).

3. Name the approvers: Slack member IDs, email addresses, or whatever identity your tool
   reports. For email, the approvers are the recipients, and each person's message carries
   single-use Approve / Reject links tied to them, so the decision is recorded in their name.
4. Tick which notification events should also go to this destination.

!!! note "Your webhook URL is a credential"
    A webhook URL contains its own secret token — anyone holding it can post into that channel.
    Kenaptic stores it like a password and never shows it again after you save it. Leaving the
    field blank keeps the one already stored.

## Notification events

Frequent notifications get ignored, so select only the events your team will act on. Per domain
workflow, you choose which events are delivered:

| Event | Sent when |
|---|---|
| **Cross-links awaiting review** | New suggested links have entered the review queue |
| **Contradictions found** | A scan found pages that state conflicting things |
| **Injection deployed** | Approved links were published back to your content |
| **A domain refused crawling** | A source blocked Kenaptic, so its content is missing |

## Requesting a decision

From the review queue, any reviewer can press **Send for approval** on a proposed link. The
domain's approvers receive the request in their tool; their answer is recorded in Kenaptic the
same way a console decision is, attributed to the person who gave it. Sending the same request
twice does not post twice: Kenaptic reports that the link is already awaiting a decision. A
deliberate **Re-send** invalidates the links in the earlier message first.

## Delivery failures

A broken channel does not affect your content. Delivery runs separately from discovery, review
and publishing, so an expired webhook or an unreachable mail server cannot block any of them.
Kenaptic reports the delivery failure so you can fix it.

## Next

- [The review loop](../getting-started/the-review-loop.md) — what happens around a decision
- [Settings & account](settings.md) — the rest of your configuration

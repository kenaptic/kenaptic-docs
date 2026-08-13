# Cross-link notifications

By default a link waits for a person to approve it. That safeguard only works if someone knows
there's something waiting. **Cross-link notifications** tell your team, in the tool they already
have open, that Kenaptic needs them.

## What you'll receive

A short message saying what happened and how much of it there is, with a button that takes you
straight to the right page in Kenaptic. For example:

> **3 cross-links awaiting review**
> Discovery finished. Approve or reject the proposed links to publish them.
> *[ Open the review queue ]*

## Choosing what you're told about

Notifications are only useful if they're rare enough to be believed. You choose which events are
worth interrupting someone for:

| Event | Sent when |
|---|---|
| **Cross-links awaiting review** | New suggested links have entered the review queue |
| **Contradictions found** | A scan found pages that state conflicting things |
| **Injection deployed** | Approved links were published back to your content |
| **A domain refused crawling** | A source blocked Kenaptic, so its content is missing |

By default Kenaptic sends the first two. A channel that pings on everything gets muted, and a muted
channel protects nothing.

## Where notifications can go

| Channel | Status | What you need |
|---|---|---|
| **Slack** | Available | An incoming webhook URL for the channel |
| **Email** | Available | Your SMTP server, configured under *Settings → Email server* |
| **Google Chat** | **Beta** | A webhook URL for the space |
| **Microsoft Teams** | **Beta** | An incoming webhook URL for the channel |

You can enable as many as you like at once — for example Slack for the docs team and email for a
manager who doesn't live in chat.

!!! info "What 'beta' means here"
    Google Chat and Microsoft Teams work and are safe to use, but they've had far less real-world
    exposure than Slack and email, and both vendors are actively changing their message formats. If
    a message ever looks wrong in one of these, it's worth telling us — that's exactly the feedback
    the beta label is asking for.

## Setting it up

1. Go to **Settings → Cross-link Notifications**.
2. Turn on **Send notifications**.
3. Tick the events you want to hear about.
4. For each channel you want to use, switch it on and paste its webhook URL (or, for email, the
   recipients).
5. Press **Send test** on that channel. A real message is sent immediately, so you'll know it works
   before you rely on it — and if it fails, Kenaptic tells you why.
6. **Save notifications**.

!!! note "Your webhook URL is a credential"
    A webhook URL contains its own secret token — anyone holding it can post into that channel. So
    Kenaptic stores it like a password and never shows it again after you save it. Leaving the field
    blank keeps the one already stored; you only need to type it again if you want to replace it.

## Approvals still happen in Kenaptic

Notifications **link** you to the review queue; they never contain Approve or Reject buttons.

This is deliberate. Approving a cross-link is the moment a change becomes real, and Kenaptic treats
it as a decision that has to be traceable to a specific signed-in person. A button in a chat channel
would mean that anyone who can post in that channel could approve on your behalf — and the audit
trail would only ever be able to record "someone in that channel". One click into the app keeps
approval tied to a real, authenticated account with 2FA behind it.

## If a channel stops working

A broken notification channel never affects your content. Delivery happens separately from the work
itself, so an expired webhook or an unreachable mail server can't block discovery, hold up a review,
or stop a link being published. Kenaptic simply reports the failure so you can fix it — use
**Send test** to check a channel at any time.

## Next

- [The review loop](../getting-started/the-review-loop.md) — what happens after you're notified
- [Settings & account](settings.md) — the rest of your configuration

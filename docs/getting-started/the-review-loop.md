# The review loop

Kenaptic's core workflow is a single repeatable loop:

<div class="grid" markdown>

**1. Propose** → **2. Review** → **3. Publish** → **4. Re-check**

</div>

## 1. Propose

After your sources are connected, Kenaptic fills the **Cross-link Review** queue with proposed
links. Each one names the two pages it would connect, the relationship between them, and a
confidence indicator to help you prioritise.

## 2. Review

Open **Cross-link Review** and work through the queue. For each proposal you can:

- **Approve** it as-is.
- **Edit** it (for example, adjust the wording of the link), then approve.
- **Reject** it if it isn't right.

You can preview the exact change before deciding. Approving a link doesn't publish it yet; it moves
it to the publish step, so you can review in a batch and publish when you're ready.

!!! tip "Prioritising the queue"
    Sort by confidence and start with the strongest proposals. Approving a handful of clearly good
    links on day one is more valuable than trying to clear the whole queue.

## 3. Publish

Approved links are published from the **Link Injection** page. Kenaptic writes each link into the
page's own source, producing a native link that works for every reader and crawler. Links are
clearly marked as Kenaptic's and can be removed cleanly at any time.

## 4. Re-check

Kenaptic re-checks your estate on a schedule. As content changes, it proposes new links and flags
ones that no longer make sense; both return to the review queue. This keeps cross-links current
without manual maintenance.

## Supporting pages

The other pages in the product support this loop:

- **Content Gaps** and **Contradictions** surface deeper content issues to fix, beyond links to add.
- **AI Readiness** reports how well machines can understand your content.
- **Link Performance**, **Analytics**, and **Reports** measure the effect of published links.
- **Audit** records every decision.

The [**Using Kenaptic**](../guide/discover.md) section covers each of these in turn.

## Notifications

Kenaptic can post to Slack, Google Chat, Microsoft Teams or email whenever links are waiting to be
reviewed, with a link straight to the queue, so you do not need to poll the queue manually. See
[Cross-link notifications](../guide/notifications.md).

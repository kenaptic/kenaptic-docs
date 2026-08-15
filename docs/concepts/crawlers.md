# Our crawlers

Kenaptic operates two crawlers. They have different jobs, read different things, and you may see
either in your access logs. This page is the reference for both: what they are, what they store,
and how to stop them.

| | **KenapticBot** | **KenapticProspector** |
|---|---|---|
| **User-Agent** | `KenapticBot/1.0 (+https://www.kenaptic.com/bot)` | `KenapticProspector/1.0 (+https://kenaptic.com/crawler)` |
| **Why it is here** | A Kenaptic customer connected this site as a content source | Public research, or someone ran a free estate scan on this domain |
| **Reads** | Pages within sources a customer chose | Public pages only, sampled |
| **Stores** | Derived metadata, personal data stripped first | Metadata only — no page bodies |
| **Typical rate** | 1 request/second per host, slower if you ask | 1 request every 2 seconds per host; up to 10/second for a 60-second estate scan |
| **Opt out** | `robots.txt` | `robots.txt` |

Both honour `robots.txt`. Neither executes JavaScript, submits forms, uses credentials, or reads
anything behind a login.

---

## KenapticBot — reading a customer's connected sources

This is the crawler doing Kenaptic's actual work. A customer connects content sources they choose
— their documentation, knowledge base, blog, forum — and KenapticBot fetches those pages so
Kenaptic can find relationships between them. The output is a plain hyperlink from one of their
pages to another.

You will see KenapticBot if a Kenaptic customer named your site as a source. That includes their
own properties, and it includes third-party sites they want to link **to**.

### What it stores

Minimal derived metadata: the URL, the title, a topic digest and an embedding. It does not
republish your content and does not store page bodies.

!!! note "Personal data is removed before anything is written down"
    KenapticBot strips personal identifiers — email addresses, phone numbers, @handles,
    usernames, bylines, profile links — from the title, body and description at the moment of
    ingestion, before storage. Everything derived afterwards is built from the cleaned text, so
    no personal data is stored and none is sent to a language model.

    This applies to every source, including sites operated by the customer who asked us to read
    them. Detection is pattern matching that runs on our own infrastructure — your text is not
    sent to a model in order to find the personal data in it.

    This is data minimisation applied everywhere, not a guarantee that pattern matching catches
    every possible form of personal data in free prose. If you would rather a page were not read
    at all, the opt-out below is immediate.

### Politeness

One request per second per host by default, and your `Crawl-delay` wins if it is slower. Requests
are spread over time rather than issued in bursts.

### Beyond robots.txt

KenapticBot also treats these as instructions not to read a page, and records the refusal:

- `X-Robots-Tag` response headers containing `noai` or `notrain`
- `<meta name="robots" content="… noai …">` in the page
- A machine-readable TDM reservation at `/tdmrep.json`
- Anything behind a login wall — an authentication challenge ends the fetch; it is never worked around

---

## KenapticProspector — mapping public content estates

This crawler answers a narrower question: **how connected is a site's public content?** It maps
which content silos a domain has — documentation, knowledge base, blog, community — and counts
the editorial links that actually run between them, discounting the navigation and footer links
every page carries.

It runs in two modes.

**Research.** We look at public content estates to understand how fragmented they typically are.
One request every two seconds per host, and it samples rather than crawling exhaustively.

**Estate scan.** Anyone can run [a free scan](https://www.kenaptic.com/) on a domain from our home
page. That crawl is deliberately small and hard-capped:

| | |
|---|---|
| At most **100 pages** | across every silo combined, per scan |
| At most **60 seconds** | the whole scan is abandoned at the deadline |
| At most **8 hosts** | subdomain probing cannot become enumeration |
| Up to **10 requests/second** per host | within that 60-second window, and your `Crawl-delay` still wins |
| **One real crawl per domain per 6 hours** | whoever asks — everyone else is served the cached result |

None of those limits can be raised by whoever ran the scan. There is no page-count parameter and
no deep-scan toggle; the cost of a scan is ours to set, not the caller's.

### What it stores

Metadata only — URLs, titles, which silo a page belongs to, and link counts between silos. It
does not store page bodies, paragraphs or extracts.

!!! info "It sees your site the way an AI crawler does"
    KenapticProspector does not execute JavaScript, on purpose. It reads exactly the HTML that
    GPTBot, ClaudeBot and other AI crawlers receive — which is the point of the exercise. If your
    content only appears after JavaScript runs, we will not see it, and neither will they.

---

## How to opt out

`robots.txt` is the opt-out for both crawlers. It is self-service, it takes effect on our next
fetch, and it needs no contact with us.

**Block both:**

```
User-agent: KenapticBot
Disallow: /

User-agent: KenapticProspector
Disallow: /
```

**Block one and allow the other** — for example, keep the free estate scan working while
declining to be used as a source:

```
User-agent: KenapticBot
Disallow: /
```

**Restrict rather than block** — slow us down, or protect part of the site:

```
User-agent: KenapticBot
Crawl-delay: 10
Disallow: /internal/
```

### What blocking KenapticBot also does

Blocking KenapticBot does more than stop future crawls. On the next daily policy pass, **any
existing Kenaptic-injected links pointing at your pages are automatically retracted**. You do not
need to ask for that separately, and you do not need to tell us.

---

## What neither crawler will ever do

- Crawl behind a login, or use credentials of any kind
- Submit a form, or bypass a paywall or any other technical access control
- Execute JavaScript
- Republish your content — the output is a hyperlink to your page
- Ignore `robots.txt`, or treat a block as advisory

---

## Verifying a request is really from us

Both crawlers identify themselves by User-Agent, and each one links to a page explaining it. Be
aware of the limit of that: **a User-Agent is a claim, not proof.** Anyone can send a request
calling itself KenapticBot, and traffic that misbehaves while wearing our name is not ours.

We do not currently publish a list of source addresses. If you are seeing traffic attributed to
either crawler that does not match the behaviour described on this page — ignoring your
`robots.txt`, crawling far faster than the rates above, requesting pages behind authentication —
please tell us. We will confirm whether it was us, and if it was, it is a bug we want to fix.

---

## Contact

Questions, complaints or removal requests: [send us a message](https://www.kenaptic.com/contact).
Removal requests are handled first, and you do not need to be a customer.

If you are reporting crawler behaviour, the useful details are the User-Agent string as your logs
recorded it, the source address, a timestamp with a timezone, and a few of the paths requested.

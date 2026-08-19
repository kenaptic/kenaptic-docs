# Kenaptic crawlers

Kenaptic operates two crawlers. They have different jobs, read different things, and you may see
either in your access logs. This page is the reference for both: what they are, what they store,
and how to stop them.

| | **KenapticBot** | **KenapticProspector** |
|---|---|---|
| **User-Agent** | `KenapticBot/1.0 (+https://www.kenaptic.com/bot)` | `KenapticProspector/1.0 (+https://kenaptic.com/crawler)` |
| **Trigger** | A Kenaptic customer connected this site as a content source | Public research, or someone ran a free estate scan on this domain |
| **Reads** | Pages within sources a customer chose | Public pages only, sampled |
| **Stores** | Derived metadata, personal data stripped first | Metadata only, no page bodies |
| **Typical rate** | 1 request/second per host, slower if `Crawl-delay` requires it | 1 request every 2 seconds per host; up to 10/second for a 60-second estate scan |
| **Opt out** | `robots.txt` | `robots.txt` |

Both honour `robots.txt`. Neither executes JavaScript, submits forms, uses credentials, or reads
anything behind a login.

---

## KenapticBot

KenapticBot serves the core product. A customer connects content sources they choose (their
documentation, knowledge base, blog, forum) and KenapticBot fetches those pages so Kenaptic can
find relationships between them. The output is a plain hyperlink from one of their pages to
another.

You will see KenapticBot if a Kenaptic customer named your site as a source. That includes their
own properties, and it includes third-party sites they want to link to.

### Stored data

Minimal derived metadata: the URL, the title, a topic digest and an embedding. It does not
republish your content and does not store page bodies.

!!! note "Personal data is removed before storage"
    KenapticBot strips personal identifiers (email addresses, phone numbers, @handles,
    usernames, bylines, profile links) from the title, body and description at the moment of
    ingestion, before storage. Everything derived afterwards is built from the cleaned text, so
    no personal data is stored and none is sent to a language model.

    This applies to every source, including sites operated by the customer who asked us to read
    them. Detection is pattern matching that runs on our own infrastructure; your text is not
    sent to a model in order to find the personal data in it.

    This is data minimisation applied everywhere, not a guarantee that pattern matching catches
    every possible form of personal data in free prose. To prevent a page being read at all, use
    the opt-out below; it takes effect on the next fetch.

### Request rate

One request per second per host by default, and your `Crawl-delay` wins if it is slower. Requests
are spread over time rather than issued in bursts.

### Additional opt-out signals

KenapticBot also treats these as instructions not to read a page, and records the refusal:

- `X-Robots-Tag` response headers containing `noai` or `notrain`
- `<meta name="robots" content="… noai …">` in the page
- A machine-readable TDM reservation at `/tdmrep.json`
- Anything behind a login wall — an authentication challenge ends the fetch; it is never worked around

---

## KenapticProspector

KenapticProspector measures how connected a site's public content is. It maps which content silos
a domain has (documentation, knowledge base, blog, community) and counts the editorial links
between them, discounting the navigation and footer links every page carries.

It runs in two modes.

**Research.** We look at public content estates to understand how fragmented they typically are.
One request every two seconds per host, and it samples rather than crawling exhaustively.

**Estate scan.** Anyone can run [a free scan](https://www.kenaptic.com/) on a domain from our home
page. That crawl is small and hard-capped:

| Limit | Detail |
|---|---|
| 100 pages maximum | across every silo combined, per scan |
| 60 seconds maximum | the whole scan is abandoned at the deadline |
| 8 hosts maximum | subdomain probing cannot become enumeration |
| 10 requests/second per host maximum | within that 60-second window, and your `Crawl-delay` still wins |
| One real crawl per domain per 6 hours | regardless of who asks; everyone else is served the cached result |

None of these limits can be raised by the caller. There is no page-count parameter and no
deep-scan toggle.

### Stored data

Metadata only — URLs, titles, which silo a page belongs to, and link counts between silos. It
does not store page bodies, paragraphs or extracts.

!!! info "JavaScript is not executed"
    KenapticProspector deliberately does not execute JavaScript. It reads the same HTML that
    GPTBot, ClaudeBot and other AI crawlers receive, so its measurement matches what those
    crawlers can see. Content that appears only after JavaScript runs is invisible to
    KenapticProspector and to those crawlers.

---

## How to opt out

`robots.txt` is the opt-out for both crawlers. It is self-service, it takes effect on our next
fetch, and it needs no contact with us.

To block both crawlers:

```
User-agent: KenapticBot
Disallow: /

User-agent: KenapticProspector
Disallow: /
```

To block one and allow the other (for example, keep the free estate scan working while declining
to be used as a source):

```
User-agent: KenapticBot
Disallow: /
```

To restrict rather than block (set a slower rate, or protect part of the site):

```
User-agent: KenapticBot
Crawl-delay: 10
Disallow: /internal/
```

### Link retraction on block

Blocking KenapticBot also retracts existing links. On the next daily policy pass, any existing
Kenaptic-injected links pointing at your pages are automatically retracted. No separate request
or notification is needed.

---

## Restrictions on both crawlers

Neither crawler will ever:

- Crawl behind a login, or use credentials of any kind
- Submit a form, or bypass a paywall or any other technical access control
- Execute JavaScript
- Republish your content — the output is a hyperlink to your page
- Ignore `robots.txt`, or treat a block as advisory

---

## Verifying crawler traffic

Both crawlers identify themselves by User-Agent, and each User-Agent links to a page describing
it. A User-Agent header does not prove origin: anyone can send a request identifying itself as
KenapticBot, and traffic that violates the behaviour described on this page is not ours.

We do not currently publish a list of source addresses. If you see traffic attributed to either
crawler that does not match this page (ignoring your `robots.txt`, crawling far faster than the
rates above, requesting pages behind authentication), report it. We will confirm whether the
traffic was ours; if it was, we treat the behaviour as a bug.

---

## Contact

Questions, complaints or removal requests: [send us a message](https://www.kenaptic.com/contact).
Removal requests are handled first, and you do not need to be a customer.

If you are reporting crawler behaviour, the useful details are the User-Agent string as your logs
recorded it, the source address, a timestamp with a timezone, and a few of the paths requested.

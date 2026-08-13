# Kenaptic documentation

The user guide published at [kenaptic.com/docs](https://www.kenaptic.com/docs/). Built with
MkDocs Material; sources in [`docs/`](docs/), navigation in [`mkdocs.yml`](mkdocs.yml).

```bash
pip install -r requirements.txt
mkdocs serve      # http://127.0.0.1:8000
```

This is a public repository because **Kenaptic adds cross-links by opening pull requests against
source files.** Linking a documentation page to a related article means editing the markdown
here — so the file has to be editable, and the pull request has to be visible for it to be worth
anything as evidence.

## Writing

One markdown file per page under `docs/`, listed in the `nav:` block of `mkdocs.yml`. The site
builds with `--strict`, so a broken cross-reference fails the build rather than shipping a dead
link.

## Publishing

The site rebuilds from the `main` branch. Merging here publishes.

## Related

- [`kenaptic-blog`](https://github.com/kenaptic/kenaptic-blog) — the articles, also public, also
  markdown. Cross-links between the two are the demonstration.

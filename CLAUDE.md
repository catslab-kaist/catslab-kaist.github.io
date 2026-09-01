# catslab-kaist.github.io

CATS Lab's (Computational Analytics of Technology and Society, KAIST) homepage. Jekyll site,
custom domain at `catslab.kaist.ac.kr`. Content structure:

- `_people/*.md` — one profile per lab member (`position: pi|gradstudent|alumni|intern`, etc.).
  Interns use `output: false` (no individual page). Each member's `## Publications` section lists
  only the papers where they appear with a `#Name` hashtag link.
- `publications.md` — all lab publications, grouped under `### <Research theme>` headings (reusing
  the themes/blurbs from Lanu's personal site, `lanukim.github.io`). Within each theme, working
  papers come first, then published works with full citations.
- `_data/news.yml` — each entry has a `headline` (short, shown on the homepage, mentions only
  current lab members by their `#Name` hashtag link) and `details` (full text, shown on `/news/`).
- `_config.yml`'s `nav` controls the top navigation.

## Checking for new publications

The cue for this is **"랩 연구 업데이트 해줘"**. When Lanu gives that cue, run this pipeline without
asking her to spell out the steps:

1. Fetch her Google Scholar profile:
   `https://scholar.google.com/citations?user=77i0fdMAAAAJ&hl=en&oi=ao`
2. Read `publications.md` and collect every entry currently marked `[working paper]` or
   `[under review]` (these appear inline after the title, e.g. `_Some Title_ [working paper]`).
3. Match each such entry against the Scholar list by author overlap + topic — titles often change
   between the draft stage and final publication, so don't rely on an exact title match.
4. For each match, fetch exact citation metadata (DOI via Crossref: `curl -s
   https://api.crossref.org/works/<DOI>`; arXiv preprints via the arXiv API/abstract page; use
   Semantic Scholar (`https://api.semanticscholar.org/graph/v1/paper/DOI:<DOI>?fields=title,abstract`)
   or the paper's own abstract page if Crossref has no abstract) — authors, journal, volume/issue,
   article number/pages, and the real publication date (prefer `published-online` >
   `published-print` > `published`).
5. Update `publications.md`: move the matched entry from the working-papers block to the
   published-works block **within the same research theme section**, replacing the `[working
   paper]`/`[under review]` tag with the full citation + `[Article](link)`, in the same format as
   neighboring published entries. Keep every `#Name` hashtag link intact (and add one for any
   co-author who is a current lab member but wasn't linked yet — check `_people/*.md` for a
   matching `name:`).
6. Add a news item to `_data/news.yml`, dated to the paper's actual publish year/month (first of
   the month), with:
   - `headline`: short, e.g. `"#Author One and #Author Two published 'Title' in Journal."` —
     only mention lab members who have a `#Name` hashtag (i.e. have a `_people/` page), never the
     full author list.
   - `details`: full author list (lab members hashtag-linked same as in `publications.md`) plus a
     1-3 sentence summary of what the paper actually found, based on its real abstract — not a
     generic restatement of the title.
7. For each lab member who co-authored the paper, add/update the citation in their `_people/*.md`
   `## Publications` section (after `## Contact`), matching the existing format there (most recent
   first, no leading year-number prefix — the year lives inside the citation itself).
8. Show her the diff (`publications.md`, `_data/news.yml`, and the affected `_people/*.md` files)
   and wait for her go-ahead before committing or pushing — never push without explicit
   confirmation.
9. If a Scholar entry doesn't match anything already in `publications.md` (a genuinely new paper
   never mentioned before, e.g. from a new collaboration), don't guess which theme section it
   belongs in or which lab members should be hashtagged — just flag it to her.

# Site to-do list (not published; excluded in _config.yml)

Everything below needs something from you. Switches live in `_config.yml`; text lives in `_data/`.

## Content only you can supply
- [ ] **Triton images.** Download `Hero 4.0 Render.JPG` and `Hero MAX.JPG` (Drive, "TR Hero Stuff") into `Portfolio_Stuff/`, then tell Claude to place them on the Triton page and card.
- [ ] **"Why this work" story.** Write 2 to 4 sentences about one real moment (idea: translating Spanish for the orphanage house parents in Tijuana). Put it in `_data/why.yml`, then set `show_why: true` in `_config.yml`.
- [ ] **"Outside the lab" specifics.** Replace the generic paragraph in `index.html` with real details (F1 team, a signature dish, a trail you ride, a movie you'd defend).
- [ ] **News.** Add or change dated lines in `_data/news.yml`. Three starter entries are already there; check the dates.
- [ ] **A "What broke" note** for the mobile manipulator and the hexapod project. There is a hidden comment at the bottom of each file in `_projects/`.
- [ ] **Availability dates.** Currently "starting summer 2027". Change to a month once you know.
- [ ] **Compress and add the ICRA demo video**, or paste a YouTube link into `_data/publications.yml` as `video:` (a "Video" button appears).

## Needs your accounts
- [ ] **Google Scholar profile.** Create one, then paste the URL into `scholar:` in `_config.yml`. A footer link appears.
- [ ] **Put code on GitHub** (shaft design script, MAE 204 controller, optimization code if your advisor agrees). Then set `show_github: true` in `_config.yml` to show a live repo list on the home page.
- [ ] **Search Console.** Verify the tag is accepted, then submit `sitemap.xml` under Sitemaps.
- [ ] **LinkedIn rewrite.** Paste the new About, headline, and experience text; update the website link to https://www.williamlh.com.
- [ ] **Cor Medical Ventures on LinkedIn** (resume wording only, no media unless your supervisor approves).

## Design decisions
- [ ] **Pick an accent color.** Preview any option by adding `?accent=HEX` (no #) to a page URL: `0a6fc2` current blue, `0f9d7a` clinical green, `e0561b` rescue orange, `0b8fa5` teal-cyan. Tell Claude your pick and it becomes the default in light and dark.
- [ ] **Decide whether to keep the hover videos, the scroll ECG line, and the expandable timeline.** All three are new.

## Check yourself
- [ ] Open the site on your phone and in both themes. Look at the nav, timeline, and cards.
- [ ] Confirm the B.S. start date (Sep 2021) and add an M.S. start date if you want one in the timeline.
- [ ] Confirm the Baja role ("Team Lead") against the winter 2023 presentation (it listed you as secretary).

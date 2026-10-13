# Track 03. Your Company List

A daily digest of new openings from the companies and boards you pick, so you stop refreshing job boards. Add or drop one any time.

**Have ready:** Ten companies you'd be glad to work for.

## The prompt

Paste this into Claude Code. Replace anything in [brackets].

```
Set up my daily job digest from digest/watchlist.md. Add these companies: [companies], and these titles: [titles]. Find each company's job board and save the link in the watchlist. Then write a small script that reads the watchlist fresh every morning at 9 and lists only new openings that match. When I tell you to add or drop a company, a board, or a title, change the watchlist. If you can't find a company's board, tell me.
```

## Changing what it watches

Everything lives in `digest/watchlist.md`: your titles, your companies, any whole boards (like a city or state jobs board), and anything to skip. Edit it yourself, or tell Claude "add Figma" or "stop watching Acme." Nothing is preloaded; the list is yours.

LinkedIn and Indeed don't allow automated searching. Use their own email alerts for those.

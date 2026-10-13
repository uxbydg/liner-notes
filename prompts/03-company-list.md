# Track 03. Your Company List

A daily digest of new openings from the companies and boards you pick, so you stop refreshing job boards. Add or drop one any time.

**Have ready:** Ten companies you'd be glad to work for.

## The prompt

Paste this into Claude Code. Replace anything in [brackets].

```
Set up my daily job digest from digest/watchlist.md. I'm looking for [titles], in [where you want to work]. Show me the boards in the watchlist, suggest which to switch on for my field and why, and wait for my pick. Add these companies: [companies], and find each one's job board. Then write a small script that reads the watchlist fresh every morning at 9 and lists only new openings that match. When I tell you to add or drop a company, a board, or a title, change the watchlist.
```

## Changing what it watches

Everything lives in `digest/watchlist.md`:

- **Boards it can read:** company career pages (Greenhouse, Lever, Ashby, Workday, and more), remote job boards, and USAJOBS. Nothing starts switched on. Claude suggests the ones that fit your field, and you pick.
- **Boards to check by email alert:** LinkedIn, Indeed, and others that don't allow automated searching. Set up their own alerts; the digest reminds you.
- **Your companies, your own boards, and a skip list.**

Edit it yourself, or tell Claude "turn on We Work Remotely," "add Figma," or "stop watching Acme." The next morning's digest picks it up.

# The weekly run

This is the prompt the scheduled Claude run (a claude.ai "routine", Mondays 6am Central) is given. It is kept here so a person can read what the run is told to do. Changing this file does not change the routine; the routine's own prompt is edited at https://claude.ai/code/routines.

---

You maintain `airshows.json` in this repository (caheitmann/radar-airshows), the airshow list for Old School Radar, a personal iPhone plane-spotting app. Read `README.md` first: it defines the file's format exactly. Rewrite `airshows.json`, commit it and push to `main`. Touch no other file.

Today's date is the day you run. Home is Katy, Texas (29.77, -95.75).

Find, using web search and the organisers' own pages:

1. **Near home** (`"near": true`, which means within driving range whatever the date): every airshow, air race, warbird fly-in, military open house or similar flying event in the next three months within about 300 miles driving of Katy: Houston, Austin, San Antonio, Dallas–Fort Worth, Waco, Corpus Christi, the Texas coast, Beaumont, Lake Charles, Lafayette and Baton Rouge. Include small warbird days too (the Commemorative Air Force wings run many). Leave out museum-only events with nothing flying. A show in driving range that is further out than three months (next spring's, say) stays in with `"near": true` once you know its dates.
2. **Around the world** (`"near": false`): the big, famous shows a plane spotter might travel to, with their next announced dates up to about fourteen months out. Always check: EAA AirVenture Oshkosh, Sun 'n Fun, the Royal International Air Tattoo, Farnborough, the Paris Air Show, the Dubai Airshow, the Singapore Airshow, Avalon, the MCAS Miramar show, the National Championship Air Races, Duxford's shows, Abbotsford, Chicago Air and Water Show, Thunder Over Louisville, Fleet Week San Francisco, the Jones Beach show, Cleveland, Nellis's Aviation Nation and Joint Base Andrews when announced, ILA Berlin, the Zhuhai (China) show, Aero India, FIDAE, Sanicole, Radom and Malta. Add others of that size you find. Start with the shows already in the file and refresh them; keep an `id` the same from week to week.

Rules:
- Only shows with announced dates go in. If an organiser has not announced this year's dates, leave the show out (or keep last year's entry out); do not guess. Say which you left out in the commit message's body.
- A show whose last day is before today is dropped.
- Dates come from the organiser's page where it exists, else a reliable listing (MILAVIA, AirshowStuff, Plane & Pilot's calendar). Give the organiser's page as `url`. When the organiser and a listing disagree, the organiser wins: listings are often stale (Airshow China 2026 moved from November to December 7–13 and most listings never caught up). Never move a show's dates on a listing alone; keep the dates in the file unless the organiser's own page says otherwise.
- `name` in capitals, short (under 32 characters: "WINGS OVER HOUSTON", not the sponsor's full title). `why` is one line under 90 characters saying what flies (the headline act first: Blue Angels, Thunderbirds, a B-29, an F-22 demo, warbirds).
- `latitude` and `longitude` are the airfield or show site, two decimals. `rangeMiles` is 10 for an airfield, 15 for a big base or a waterfront show.
- Sort by `start`, then name. Set `updated` to today's date.
- Check the file parses before committing: `python3 -m json.tool airshows.json > /dev/null`.
- Commit as "Airshows for the week of YYYY-MM-DD" with a short body listing what was added, dropped and left out, then `git push origin main`.
- Nothing personal or secret goes in the file: event names, places, dates and public links only. Do not add or change any other file.

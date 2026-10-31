# Radar airshows

The airshow list for Old School Radar, a personal iPhone plane-spotting app. One file, `airshows.json`, rewritten once a week by a scheduled Claude run that searches the web for upcoming airshows near Katy, Texas (the next three months, within about 300 miles) and the big ones around the world. The app fetches the raw file and shows them in its TRAVEL tab with their dates.

Nothing here is private: event names, places, dates and the organisers' links.

## The file

```json
{
  "updated": "2026-10-31",
  "airshows": [
    {
      "id": "wings-over-houston-2026",
      "name": "WINGS OVER HOUSTON",
      "venue": "Ellington Field",
      "place": "Houston, TX",
      "latitude": 29.61,
      "longitude": -95.16,
      "start": "2026-10-31",
      "end": "2026-11-01",
      "url": "https://wingsoverhouston.com",
      "why": "Blue Angels, warbirds, the Tora! Tora! Tora! show",
      "rangeMiles": 10,
      "near": true,
      "open": "08:00",
      "close": "16:00",
      "timeZone": "America/Chicago"
    }
  ]
}
```

- `id`: letters, digits and dashes, unique, stable from week to week (name plus year).
- `name`: in capitals, short enough for a phone row (under 32 characters).
- `place`: city and state, or city and country outside the US.
- `latitude`, `longitude`: the airfield or show site, two decimals.
- `start`, `end`: the show days (YYYY-MM-DD), the same day for a one-day show.
- `url`: the organiser's page.
- `why`: what flies, one line under 90 characters.
- `rangeMiles`: how wide to set the radar there (10 for an airfield, 15 for a big base or a waterfront show).
- `near`: true when it is within driving range of home (about 300 miles), false for the world list.
- `open`, `close` (optional): gates open and the show's end on a public day, "HH:MM" 24-hour in the show's own local time, from the organiser. Leave both out when the organiser hasn't published hours; never guess.
- `timeZone` (optional, required when `open` is given): the venue's IANA time zone, like "America/Chicago", "Europe/London", "Asia/Dubai". The app shows LOCAL TIME next to the hours when it isn't the phone's zone.
- `confirmed` (optional): false when the dates came from a listing rather than the organiser. The app ignores it.

Shows whose `end` has passed are dropped. The list is sorted by `start`. The weekly run's instructions are in `ROUTINE.md`.

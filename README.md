# excellenceintech.org

Source for [excellenceintech.org](https://excellenceintech.org), the Excellence in Tech honor society site.

The site is one static page (`index.html`) plus event photos in `photos/`. Netlify deploys the `claude/live` branch automatically. Every push to that branch goes live within a minute or two.

## Layout

- `index.html` holds all the markup, CSS and JavaScript.
- `photos/` has two sizes of every gallery photo: `-800.jpg` for the grid and `-1600.jpg` for the full-size viewer.
- `netlify.toml` tells Netlify to publish the repo root with no build step.

## Events

Events live in `index.html` between `<!-- EVENTS:START -->` and `<!-- EVENTS:END -->`, newest first. Each event is a `<div class="event" data-date="YYYY-MM-DD">` block:

- **Upcoming events** use a `btn solid` button labelled **Register**, and their meta line starts with the weekday and date.
- **Past events** use a plain `btn` button labelled **View Event**, and their meta line starts with `Past event ·`.

A weekly scheduled task checks Raj's email for new Excellence in Tech Luma links. It adds or updates events here and pushes to `claude/live`.

## Forms

The Apply and Nominate forms post to a Google Apps Script web app (`ENDPOINT` in the script block). That app writes to the submissions Google Sheet and emails the team. Don't change `ENDPOINT` unless the script is redeployed.

## Photos

Gallery photos come from the Excellence in Tech group on Tribe. To add more:

1. Resize each photo to 800px and 1600px wide as JPEG.
2. Save them to `photos/` as `eit-<event>-<nn>-800.jpg` and `eit-<event>-<nn>-1600.jpg`.
3. Add a tile to the `#photo-grid` in `index.html`, and a filter button for any new event.

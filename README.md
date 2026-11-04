# SAT Predictor

**Amateur radio satellite pass predictor that runs entirely in your browser.**

👉 **Live:** [sq5wbw.github.io/satpredictor](https://sq5wbw.github.io/satpredictor/)

SAT Predictor shows the upcoming passes of amateur radio satellites over your grid locator for the next 24 hours: when each satellite rises, how high it climbs, where to point your antenna, and which frequencies to use. It is a single HTML file with no server, no account and no installation.

## Features

- **Pass list for the next 24 hours.** AOS time, pass duration, countdown to AOS, maximum elevation and azimuth path (AOS → max → LOS) for each pass.
- **Live passes at a glance.** Satellites currently above the horizon are marked **QRV**, show their live elevation and azimuth, and have a progress bar on the left edge of the row that drains from AOS to LOS.
- **Sky plot.** Click a pass to open a polar plot of its track with AOS, max and LOS times and the satellite’s current position.
- **Frequencies and notes.** Uplink, downlink, beacon, mode and operating notes for every satellite (for example, SO-50’s 74.4 Hz arming tone).
- **Mode filters.** Show or hide FM, SSB (linear transponders) and DIG (packet, APRS, SSTV, telemetry) satellites.
- **Rotatable compass.** Drag the sky plot to match the way you are facing. The rotation is remembered.
- **Phone compass.** On a phone, turn on *Compass* and the sky plot follows the phone’s magnetometer, so the plot always matches the real sky. Magnetic declination is corrected automatically (default +6°, suitable for Poland), and you can fine-tune the correction by dragging the plot.
- **Responsive design.** Works on desktop and mobile, in light and dark mode.
- **English and Polish.** Switch with **EN | PL** (top right on desktop, in the footer on mobile). The choice is remembered.

## How to use

1. Open [sq5wbw.github.io/satpredictor](https://sq5wbw.github.io/satpredictor/).
2. Click the **Grid** field and enter your Maidenhead locator (4 or 6 characters, e.g. `KO02` or `KO02OC`). You can also link directly to a locator: `https://sq5wbw.github.io/satpredictor/#KO02OC`.
3. Click any pass to see its frequencies and sky plot.

Your locator, filters, language and compass settings are stored only in your own browser.

## Orbital data (TLE)

The page downloads current Two-Line Element sets automatically and refreshes them every 24 hours:

- [CelesTrak](https://celestrak.org/) – the *amateur* group, plus individual satellites by NORAD number,
- [AMSAT](https://www.amsat.org/tle/current/nasabare.txt) – `nasabare.txt`.

Some browsers block the download from AMSAT. If a satellite in the footer list is greyed out, its orbital data is missing: use **Download TLE file**, save `nasabare.txt`, then load it with **Load TLE file**.

## Satellites and frequencies

The satellite list (about 40 satellites) and NORAD numbers were checked against the AMSAT TLE distribution. Frequencies come from the [AMSAT frequency lists](https://www.amsat.org/live-fm-satellites/) (FM, linear, digipeater, image and testing satellites) and the [JE9PEL satellite list](https://www.ne.jp/asahi/hamradio/je9pel/satslist.htm). Satellite status changes often, so check [AMSAT Live OSCAR Satellite Status](https://www.amsat.org/status/) before operating. Each satellite’s NORAD number links to its page on [N2YO](https://www.n2yo.com/).

To add or change a satellite, edit the `SATS` list near the top of the second `<script>` block in `index.html`. Each satellite is one line with its name, NORAD number, mode and frequencies.

## Running locally

Download `index.html` and open it in a browser. Everything works offline once the TLE data has been loaded, except the phone compass: browsers only give access to the magnetometer on pages served over **https** (such as GitHub Pages). On iPhone, Safari asks for permission each time the compass is turned on.

## Technology

- One self-contained HTML file: HTML, CSS and plain JavaScript, no build step.
- Orbit propagation with [satellite.js](https://github.com/shashwatak/satellite-js) (SGP4, MIT license), embedded in the file.
- Font: [Recursive](https://www.recursive.design/) from Google Fonts, with a system font fallback.

## Credits

SAT Predictor was written from scratch as a browser-only tool by SQ5WBW, with the help of AI (Claude by Anthropic).

Thanks to CelesTrak, AMSAT, JE9PEL and N2YO for the data that makes this possible.

---

© SAT Predictor by SQ5WBW · 73!

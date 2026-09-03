<p align="center">
  <img src="art/readme-figure.webp" width="720"
       alt="A golfer at the top of the backswing, the skyline behind them torn into bands of datamosh">
</p>
<p align="center"><sub>PLATE 02 · THE GOLFER · GENERATED IMAGE, DATAMOSH TRANSFER</sub></p>

# Albie

**A caddie who has already walked the course a thousand times.**

Albie reads everything ever written, filmed or mapped about a golf course, official
hole guides, tour coverage, caddie videos, member forums and OpenStreetMap geometry,
and compiles it into conditional rules rather than a game plan. On the tee it asks
what you are actually facing, the wind, the pin, the lie, the last shot, and answers
with one club, one target and one warning. It is aimed at the courses you have never
played, where an app that learns from your own shot history has nothing to learn from.

**Try it: https://maahirbr.github.io/albie/**

Everything runs in your browser. Your profile and your rounds stay on your phone, and
the app works with no signal once it has loaded.

## Courses

<!-- COURSES:BEGIN -->
| Course | Holes | Sources | Surveyed map | Greens | Recovery intel |
| --- | --- | --- | --- | --- | --- |
| Bethpage Black Course | 18 | 16 | yes | no | no |
| Carnoustie Golf Links · Championship Course | 18 | 9 | yes | yes | yes |
| Classic Golf & Country Club (Ridge & Valley) | 18 | 11 | no | no | no |
| Delhi Golf Club · Lodhi Course | 18 | 30 | yes | yes | yes |
| DLF Golf & Country Club · Gary Player Course | 18 | 9 | no | yes | yes |
| Heritage Golf Club · La Réserve Golf Links | 18 | 12 | no | no | no |
| Heritage Golf Club · Le Château Course | 18 | 11 | yes | no | no |
| Jaypee Greens Golf Course (Greater Noida) | 18 | 9 | no | no | no |
| Kingsbarns Golf Links | 18 | 13 | yes | no | no |
| Pebble Beach Golf Links | 18 | 18 | yes | no | yes |
| Qutub Golf Course | 18 | 11 | no | yes | no |
| Rutgers University Golf Course | 18 | 9 | no | no | no |
| The Old Course, St Andrews | 18 | 10 | yes | yes | yes |

13 courses ingested. Every one carries 18 conditional holes; the columns say what is real underneath them, not what was promised.

**Known thin.** These fall back to generic trouble advice because no per-hole recovery intel has been compiled yet: Bethpage Black Course, Classic Golf & Country Club (Ridge & Valley), Heritage Golf Club · La Réserve Golf Links, Heritage Golf Club · Le Château Course, Jaypee Greens Golf Course (Greater Noida), Kingsbarns Golf Links, Qutub Golf Course, Rutgers University Golf Course.
<!-- COURSES:END -->

## Testing it

Albie is only as good as the rounds people put through it, so the loop is short:

1. Open the link on your phone and add it to your home screen. It runs offline from there.
2. Fill in Profile once. Carry numbers off a launch monitor are ideal, honest guesses are fine.
3. Play. On each shot, set the situation and take the call.
4. Rate the call, one to five, and add a line if it was wrong. That rating is the whole point.
5. In Log, tap **Export**. It saves a JSON file, and falls back to your clipboard or an
   on-screen copy box if the browser blocks downloads. Send it back.

On an iPhone, Export lands in Safari's download sheet: choose Save to Files, then send
the file from there. If nothing saves, the copy box is the fallback, and it carries the
same data.

Exports from any build are readable, including old ones and locally saved copies, so
you never need to be on the current version to send something useful.

## What is under it

- **Conditional knowledge, not a plan.** Every hole is a set of rules that fire on live
  state. A prose game plan was rejected early for being generic.
- **Sources are triangulated and dated.** One source per hole is not enough. Facts carry
  a source tag and a staleness judgment, and conflicts between sources are flagged rather
  than quietly merged.
- **Real geometry where it exists.** Surveyed hole polygons drive distance and the
  tap-to-place map. Where a green is traced by eye from imagery it is drawn dotted and
  labelled approximate.
- **Member tees are the default.** Championship numbers are labelled and translated, and
  holes whose character changes by tee say so.

## The v2 engine, as measured

A second engine lives at [/v2/](https://maahirbr.github.io/albie/v2/) so the two can be
compared rather than argued about. It was graded on 9,900 matched situations across all
courses. The engines disagreed on 25% of them, and 1,313 of those disagreements sit on
holes with real surveyed geometry and were simulated 500 shots deep per choice.

The wind and temperature half of v2 is better under every physics model tried, including
one built from v1's own assumptions and one with wind damped 30%. That part is robust.

The buried-lie half is not settled. Its verdict flips sign with the assumed carry loss:
at 22 yards v2 is far better, at 15 yards v1 is slightly better. That is the simulator
recovering its own assumption, not measuring the world. The real finding is that the loss
varies shot to shot, so a buried lie should bias the target short of the pin, and neither
engine does that yet.

So v2's wind and temperature maths are promoted into the main app. Buried lie and stimp
stay in the fork until a real round settles them.

## Status

This page hosts the built app. The knowledge pipeline, ingestion, per-tee scorecards,
geometry extraction and the decision engine, lives in the main project and opens up as it
is cleaned for release. Course data carries source tags and honest confidence levels, and
the trust card in the app shows them.

Open source, built for the love of golf.

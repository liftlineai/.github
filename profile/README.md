# LiftLine

**Predicting lift lines at ski resorts, so you can stop guessing which chair to walk to.**

[liftlineai.app](https://liftlineai.app) · [dev build](https://dev.liftlineai.app) · [lucas@liftlineai.app](mailto:lucas@liftlineai.app)

---

You have found the org. Everything in it is private, which you have probably already discovered by clicking around and finding nothing. Here is what is behind the curtain, described vaguely enough to be interesting and specifically enough to be true.

## What it does

You are standing at the base at 9:40 on a powder day. Six lifts. One of them has a twelve minute line and one of them has nothing, and the difference is worth an entire extra run. LiftLine tells you which is which, per lift, per hour, before you commit to the walk.

## How it works, roughly

**One LLM call per resort per day.** Not per request, not per lift — one. It reads the weather, the snow, the road conditions, the season calendar, and the day of the week, and produces an hourly wait curve for every lift on the mountain. Doing this cheaply is most of the trick.

**Then it corrects itself against reality.** Resort webcams get pulled, a vision model counts the people in the lift maze, and the day's predictions get nudged toward what is actually happening. This half runs with no LLM in the loop at all, which is the only reason it can run continuously.

**There is no backend server.** None. Every client reads Postgres directly. The apps do not call an API we wrote, because we did not write one. This sounds like a shortcut and is in fact the single best architectural decision in the project.

**There is a mountain graph.** Runs and lifts ingested from OpenStreetMap, attached to each other, draped over real elevation data, so the system knows that this blue run feeds that chair and roughly how long it takes to get down. Terrain parks remain an unsolved problem and are currently, embarrassingly, just blue runs.

**There is a simulator.** Synthetic riders with itineraries and preferences, choosing lifts, queueing, and going home early when it rains. It exists to compete with the LLM predictor and eventually replace it. The two are scored head to head against real observed waits. So far it is a fair fight.

**The whole thing runs on a Mac mini.** In a house. On residential internet. This is not a temporary arrangement pending real infrastructure; it is the infrastructure, and it has been more reliable than the cloud cron it replaced.

## The repos

You cannot open any of these. You can read the names and speculate.

| | |
|---|---|
| `ios` | The app. SwiftUI, widgets, a watch companion. The main event. |
| `web` | React and Vite. The thing at liftlineai.app. |
| `engine` | Python. Prediction, collection, computer vision, simulation. Where the interesting problems live. |
| `supabase` | Schema and migrations. Quietly the most important one, since it is the contract everything else is written against. |
| `docs` | More words than any solo project has business generating. |
| `creative` | Brand and campaign work. |

## Have a look

- **[liftlineai.app](https://liftlineai.app)** — the real thing
- **[dev.liftlineai.app](https://dev.liftlineai.app)** — the unstable one, where features go before they are ready. It serves a `robots.txt` telling every crawler to go away. You are not a crawler, so consider yourself the exception, and do not be surprised by what you find.

## Getting in touch

**[lucas@liftlineai.app](mailto:lucas@liftlineai.app)**

Resort operator, skier with an opinion, or someone who wants to argue about queueing theory — all equally welcome. Also findable as [@Krazycatt](https://github.com/Krazycatt) here on GitHub.

<sub>Built by one person and a great deal of compute. Not affiliated with any resort, which is why the predictions are honest.</sub>

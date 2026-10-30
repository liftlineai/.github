# LiftLine

**Predicting lift lines at ski resorts, so you can stop guessing which chair to walk to.**

[liftlineai.app](https://liftlineai.app) · [Snowcat](https://getsnowcat.app) · [lucas@liftlineai.app](mailto:lucas@liftlineai.app)

---

You are standing at the base at 9:40 on a powder day. Six lifts. One of them has a long line and one of them has nothing, and the difference is worth an extra run. Snowcat tells you which is which, per lift, per hour, before you commit to the walk.

The engine runs the simulation, the collectors, and the day, and writes one Postgres database. Snowcat and the signed-in browser app read that database. Liftie is the assistant those apps talk to. Platform is the public API and the console.

## Snowcat 1.6.28

Snowcat for iPhone, version 1.6.28, launches November 6, 2026. SwiftUI, an offline cache, home-screen widgets, and trips. The watch companion is parked outside the app target.

[App Store](https://apps.apple.com/us/app/snowcat-ski-maps-lift-waits/id6766647166)

## The repos

The repositories are private.

| | |
|---|---|
| [`ios`](https://github.com/liftlineai/ios) | Snowcat for iPhone. |
| [`engine`](https://github.com/liftlineai/engine) | Prediction, collection, and simulation. |
| [`supabase`](https://github.com/liftlineai/supabase) | Schema, migrations, and edge functions. The database the other repos share. |
| [`liftie`](https://github.com/liftlineai/liftie) | Snowcat's assistant: the chat service, its tools, and its MCP fronts. Wire contract: [`Backend/liftie/CONTRACT.md`](https://github.com/liftlineai/liftie/blob/main/Backend/liftie/CONTRACT.md). |
| [`Platform`](https://github.com/liftlineai/Platform) | Public API at [api.liftlineai.app/platform/v1](https://api.liftlineai.app/platform/v1). Console at [platform.liftlineai.app](https://platform.liftlineai.app). |
| [`admin`](https://github.com/liftlineai/admin) | Analytics, Ops, Health, and Snowcat operations. |
| [`docs`](https://github.com/liftlineai/docs) | Architecture, guides, and runbooks. Legal text for the site and the app is generated from here. |
| [`web`](https://github.com/liftlineai/web) | Public site: company, product, legal, and the Trust Center. |
| [`web-app`](https://github.com/liftlineai/web-app) | Signed-in browser app at [ride.liftlineai.app](https://ride.liftlineai.app). |

Also here: [`snowcat-backend`](https://github.com/liftlineai/snowcat-backend) for push notifications and the off-season report, [`android`](https://github.com/liftlineai/android) for the Android client, [`creative`](https://github.com/liftlineai/creative) for brand and campaigns, and [`liftline-legacy`](https://github.com/liftlineai/liftline-legacy) for the monorepo these were split from.

## What runs on a change

Engine's suite runs all eight Python suites on every pull request and every push to `main`. Admin's suite does the same for its Python tests, frontend unit and integration tests, and the production build. Engine still runs an older, smaller test workflow on `dev`.

`project-sync` in this repository files issues from engine, supabase, ios, and docs onto the org project. liftie and Platform do not define GitHub workflows.

## Have a look

- [liftlineai.app](https://liftlineai.app) — the public site
- [Snowcat](https://getsnowcat.app) — the app
- [ride.liftlineai.app](https://ride.liftlineai.app) — the signed-in browser app
- [platform.liftlineai.app](https://platform.liftlineai.app) — the API console

## Getting in touch

**[lucas@liftlineai.app](mailto:lucas@liftlineai.app)** · [@TheTorchicken](https://github.com/TheTorchicken)

<sub>Built by one person. Not affiliated with any resort.</sub>

# Contributing

These are the defaults for every repo under argamboad. A repo's own docs win where they say more
(`docs/WAYS_OF_WORKING.md`, `CLAUDE.md`, its own CONTRIBUTING).

## The work
- **An issue first**, in the house shape: *What* · *Done when* · *Cost* · *Undo* · *Ref* (the "Task" form does it).
- **One commit per issue**, its message naming the issue (`Closes #N`) and the verdict below; **one pull request
  per milestone**, into `develop`. Nothing is pushed to `main` directly.
- **Tests first.** The failing test comes before the code that makes it pass.
- **App-exclusive or generic?** Decide before changing anything. App-exclusive (its UI, brand, config, its own
  slices) is changed in the app only. Generic (platform code, a test harness, a CI step, a tool — anything a sibling
  app would also need) is changed in the platform first, then ported to every app. The verdict goes in the commit.

## CI
A pull request runs the web gates. The device legs (Android, Windows, Apple) and the deploys run only from a manual
"Run workflow" — say what a run costs in minutes before starting one. The gates are the platform's reusable workflow
(`argamboad/perezosoft-platform/.github/workflows/app-ci.yml`); a repo's `ci.yml` calls it at a platform tag.

## Secrets
Real values live only in the gitignored `.env`; nothing secret is committed, and the secret scan runs on every pull
request.

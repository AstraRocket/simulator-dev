# AstraRocket (dev)

**▶ [Launch the dev build](https://astrarocket.github.io/simulator-dev/)**

This repository publishes the **dev** build of [AstraRocket](https://github.com/AstraRocket/simulator), the browser-based UI for the OpenRocket engine. The dev site runs the `dev` branch of [AstraRocket/simulator](https://github.com/AstraRocket/simulator), where development happens, so it is the newest build there is: changes show up here first, before the [beta site](https://astrarocket.github.io/simulator-beta/) and long before the [production site](https://astrarocket.github.io/simulator/).

There is no app source here. This repository exists because GitHub Pages gives each repository one site, so the dev build needs a repository of its own to publish to.

## Using the dev build

- **Expect things to break.** The dev build is work in progress that has passed the pull request checks and nothing more. A feature can be half done, and a build can be worse than the one before it. Use the [production site](https://astrarocket.github.io/simulator/) for anything you rely on, and the [beta site](https://astrarocket.github.io/simulator-beta/) to try what is coming next.
- **Your data is kept apart from the other sites.** The dev build uses its own browser storage, so rockets, motors, materials and settings saved here do not show up on the production, beta or hotfix sites, and nothing you do here touches your production designs. Move a design between them by exporting a `.ork` from one and importing it in the other.
- **Saved data may not survive.** A dev build can change how designs and settings are stored before that change is final. Export anything you want to keep.
- **It can be installed separately.** The installed app, its name and its version are labeled dev, so it can sit beside the production install.
- **Version numbers name the build.** A dev version reads like `1.2.3-dev.45`, where the last number is the deploy run. Include it when reporting a problem.

## Reporting problems

Open an issue on [AstraRocket/simulator](https://github.com/AstraRocket/simulator/issues), not here, and include the version shown in the app.

## How the site is deployed

The build itself lives in the main repository, in [`.github/workflows/channel-deploy.yml`](https://github.com/AstraRocket/simulator/blob/dev/.github/workflows/channel-deploy.yml) on the `dev` branch. This repository's [`.github/workflows/deploy-dev.yml`](.github/workflows/deploy-dev.yml) only calls it, with `channel: dev`.

To publish the dev build:

1. Open **Actions → Deploy dev** in this repository.
2. Click **Run workflow**.

The called workflow checks out the `dev` branch of AstraRocket/simulator, builds the app and its docs with the `/simulator-dev/` base path and `APP_CHANNEL=dev`, and deploys the result to this repository's Pages site. Because a called workflow runs as its caller, the run, its Pages deployment and its token all belong to this repository; the main repository is only read. Nothing in the main repository can start this deploy, so it cannot publish over the production site.

### Setup

Pages for this repository must be set to deploy from **GitHub Actions** (Settings → Pages → Build and deployment → Source).

# HârnWorld Location Module: Hundholt
[![Version (latest)](https://img.shields.io/github/v/release/toastygm/hm-loc-hundholt)](https://github.com/toastygm/hm-loc-hundholt/releases/latest)
[![Forge Installs](https://img.shields.io/badge/dynamic/json?label=Forge%20Installs&query=package.installs&suffix=%25&url=https%3A%2F%2Fforge-vtt.com%2Fapi%2Fbazaar%2Fpackage%2Fhm-loc-hundholt&colorB=4aa94a)](https://forge-vtt.com/bazaar#package=hm-loc-hundholt)
[![GitHub downloads (latest)](https://img.shields.io/badge/dynamic/json?label=Downloads@latest&query=assets[?(@.name.includes('zip'))].download_count&url=https://api.github.com/repos/toastygm/hm-loc-hundholt/releases/latest&color=green)](https://github.com/toastygm/hm-loc-hundholt/releases/latest)

Hundholt Manor is a "Location Module" for the Foundry VTT system. This location module
is designed to depict the Hundholt Manor and Fethael Hundred moot in the far north of
he Kingdom of Kaldor, on the island of Hârn in the [HârnWorld](https://columbiagames.com/harnworld/) fantasy
setting; however, this manor could be adapted to exist anywhere in any fantasy setting.

Although designed for use with the [HârnMaster](https://foundryvtt.com/packages/hm3)
system, this module is mostly system-agnostic.  Detailed descriptions of the actors
has been provided in journal entries to facilitate conversion to other game systems.

# Maps

The original maps from this work have been used as inspiration, and new maps have been
designed specifically to meet the requirements of the VTT environment.  The following
maps are part of this module.

## Hundholt Village

Map of Hundholt Village, including the manor.

<img src="assets/scenes/hundholt-village.webp" alt="Hundholt Village" width="600"/>

## Rawyn Farm

Ground level.

<img src="assets/scenes/rawyn-farm-ground.webp" alt="Rawyn Farm Ground" width="600"/>

Upper level.

<img src="assets/scenes/rawyn-farm-upper.webp" alt="Rawyn Farm Upper" width="600"/>

## Hundholt Manor

Ground level.

<img src="assets/scenes/hundholt-manor-ground.webp" alt="Hundholt Manor Ground" width="600"/>

Upper level.

<img src="assets/scenes/hundholt-manor-upper.webp" alt="Hundholt Manor Upper" width="600"/>

Top level.

<img src="assets/scenes/hundholt-manor-top.webp" alt="Hundholt Manor Top" width="600"/>

Roof level.

<img src="assets/scenes/hundholt-manor-roof.webp" alt="Hundholt Manor Roof" width="600"/>

# Credits

This module is made possible by the hard work of HârnWorld fans,
and is provided at no cost. This work is an adaptation of the article
[Hundholt](https://www.lythia.com/harnworld/settlements/hundholt/) available
at the HârnWorld fan site [Lythia.com](https://www.lythia.com/).

**Writer:** Joe Adams

**Original Maps:** George Kelln

**Heraldry:** Matthias Janssen

With Thanks to Robert Barfield

**Adapted to Foundry VTT:** Tom Rodriguez

This module is "[Fanon](https://www.lythia.com/about/publishing-fan-written-material/)",
a derivative work of copyrighted material by Columbia Games Inc. and N. Robin Crossby.

Some assets used to create the maps in this module are from
[Forgotton Adventures](https://www.forgotten-adventures.net/).


# Development

Requires Node.js >= 24.

## Project structure

- `assets/packs/<name>/unique/` — source JSON files for each compendium pack
- `assets/templates/module.template.json` — module manifest template (version/URLs are injected at build time from `package.json`)
- `scripts/init.js` — ScenePacker integration
- `utils/` — build scripts

## Common tasks

```sh
npm install                  # install dependencies (first time / after pulling)
npm run deploy:qa            # build and deploy to local QA Foundry instance
npm run deploy:release       # build and create build/dist/module.zip
npm run release              # create GitHub release (needs GITHUB_TOKEN)
npm run clean                # remove build/
```

## Making content changes

Edit the JSON files in `assets/packs/<name>/unique/`. These are the source of truth — LevelDB packs are compiled from them at build time.

## Deploying locally for testing

Set environment variables for your Foundry data paths (in `.env.local` or your shell):

```
FOUNDRYVTT_DEV_DATA=/path/to/foundry/dev
FOUNDRYVTT_QA_DATA=/path/to/foundry/qa
FOUNDRYVTT_PROD_DATA=/path/to/foundry/prod
```

Then `npm run deploy:qa` (or `:dev` / `:prod`) will build and rsync to that instance.

## Releasing

1. Bump the version in `package.json`
2. Commit and push to `main`
3. `npm run deploy:release` — builds and creates `build/dist/module.zip`
4. `export GITHUB_TOKEN=$(gh auth token)` (or set in `.env.local`)
5. `npm run release` — creates a GitHub release with `module.zip` and `module.json` attached

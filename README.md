# Counter-Strike 2 · Practice Configuration

My practice config for Counter-Strike 2. A single command sets up a private server for practicing grenades, spray, and positions: infinite money and ammo, buy anywhere, grenade camera, bullet impacts, noclip, and bot controls.

> Ported from my original CS:GO practice config. Version 2.0 updates it for CS2 (see the [changelog](#changelog)).

---

## Installation

1. Download `practice.cfg`.
2. Put it in your CS2 `cfg` folder. CS2 uses a **new location**. The old CS:GO `csgo\cfg` folder no longer works:

   | OS | Path |
   |---|---|
   | Windows | `C:\Program Files (x86)\Steam\steamapps\common\Counter-Strike Global Offensive\game\csgo\cfg\` |
   | Linux | `~/.local/share/Steam/steamapps/common/Counter-Strike Global Offensive/game/csgo/cfg/` |

   > Quick way: in Steam, right-click **Counter-Strike 2 → Manage → Browse local files**, then open `game` → `csgo` → `cfg`.

3. Turn on the console: **Settings → Game → Enable Developer Console → Yes**. Open it with the <kbd>`</kbd> / <kbd>~</kbd> key.

## Usage

1. Start an offline map or a private match that you host.
2. Once the map has loaded, open the console and run:

   ```
   exec practice
   ```

The config turns on `sv_cheats` and removes all bots, then ends warmup and restarts the round. A help menu prints to the console.

---

## Binds

| Key | Action |
|---|---|
| <kbd>Mouse 4</kbd> | Toggle noclip (fly through walls) |
| <kbd>Mouse 5</kbd> | Rethrow your last grenade |

> These **replace** whatever you already had on Mouse 4 and Mouse 5, and CS2 saves them to your settings. To change them, edit the two `bind` lines in `practice.cfg` before running it.

## Commands

Type these in the console after running `exec practice`.

### Grenades & tools

| Command | Effect |
|---|---|
| `nades` | Give yourself every grenade (HE, flash, smoke, incendiary, molotov, decoy) |
| `rethrow` | Rethrow your last grenade from the same spot |
| `showray` | Draw a ray from where you stand to where you're looking |

### Bots

| Command | Effect |
|---|---|
| `terrorist` | Add a T bot |
| `counter` | Add a CT bot |
| `place` | Move a bot to where you are looking |
| `freeze` | Freeze / unfreeze all bots (toggle) |
| `mimic` | Bots copy your movement (toggle) |
| `kickbots` | Remove all bots |

---

## What the config sets

| Setting | Value |
|---|---|
| Cheats | On (`sv_cheats 1`) |
| Damage | You take damage but can't die (`buddha 1`) |
| Position display | On (`cl_showpos 1`) |
| Grenade camera | Picture-in-picture view that follows your grenade |
| Grenade trail | Visible for 8 s |
| Bullet impacts | Shown for 10 s |
| Money | $60,000 start and max |
| Buying | Anywhere, at any time |
| Ammo | Infinite, no reload |
| Grenades | Carry up to 5 |
| Round time | 60 min (normal, bomb, and hostage maps) |
| Freeze time | 0 s |
| Bots | Removed on start |

---

## Troubleshooting

- **`exec: couldn't exec ... unable to read file`**: the file is in the wrong folder. It must be in `game\csgo\cfg`, not `csgo\cfg`. Also check that Windows didn't save it as `practice.cfg.txt`.
- **"Can't use cheat command"**: you have to host the match yourself. Cheat commands don't work on official or community servers.
- **Settings reset after changing map**: run `exec practice` again after each map load.

---

## Changelog

### v2.0 (CS2 port)
- Updated install path for CS2 (`game\csgo\cfg`).
- `sv_cheats 1` now runs **first**. In v1.0, `god` ran before cheats were enabled, so it never worked.
- `god` replaced with `buddha 1`. `god` is unreliable in CS2, and as a toggle it switched itself off when you ran the config twice.
- `sv_grenade_trajectory` and `sv_grenade_trajectory_time` (removed in CS2) replaced with `sv_grenade_trajectory_prac_pipreview` and `sv_grenade_trajectory_prac_trailtime`. The trail time is set to 8 s, the CS2 maximum.
- **Fixed:** the bind lines used curly quotes (`“ ”`), which the console doesn't accept.
- **Fixed:** the `kick` alias clashed with the built-in `kick` command. It's now `kickbots`.
- `freeze` and `mimic` are now on/off toggles. Previously they could only turn on.
- Mouse 5 now rethrows your last grenade (`sv_rethrow_last_grenade`, new in CS2). `cast_ray` is still available as `showray`.
- Added `mp_roundtime_hostage`. `bot_quota 0` now runs before `bot_kick`, so bots don't refill.
- Added a console help menu.

### v1.0
- Original CS:GO release.

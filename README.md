# RoleplayEngine

An AI game master for Shadowrun that runs your table in a Discord channel. Claude is the GM; the dice, stats, gear
and money live in a hard ledger it can't fudge, and the story is remembered in an energy graph, so what mattered
stays hot and old threads come back when they're touched. NPCs keep living off-screen between turns, there's
optional AI art (portraits, places, maps) and a 3D browser for the world's memory.

## What you need

- Python 3.11 or newer
- A Discord bot (developer portal) with the **Message Content** intent turned on
- An Anthropic API key
- An OpenAI API key if you want art (optional)

## Setup

Windows:

```
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
```

Linux / macOS:

```
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Copy `config.example.toml` to `config.toml` and fill in your keys. Or skip the file and set the environment
variables instead: `DISCORD_BOT_TOKEN`, `ANTHROPIC_API_KEY`, `OPENAI_API_KEY`. The file wins if both are set.
`config.toml` is in `.gitignore` - keep it that way.

## Run

The commands below expect the venv to be active (the `activate` line above, once per terminal).

- Windows: double-click `RoleplayEngine.bat`. That opens the dashboard; start the bot from its Bot page.
  `RoleplayEngine.bat bot` / `stop` / `status` do it from a command line (no activating needed).
- Anywhere: `python -m roleplay.discord_bot` runs the bot, `python -m roleplay.dashboard --browser` opens the
  dashboard in your browser (`--serve` for just the server).
- `python -m roleplay` plays a world in the console, no Discord needed.

Worlds are saved in `campaigns/` (created on first run).

## Play

Invite the bot to your server (scopes `bot`). It needs to read and send messages, read message history, add
reactions, embed links, attach files, create public threads and send messages in them, and manage webhooks - the
NPCs talk through one. Then in a channel:

```
!rp start demo      bind this channel to a world (demo and rage are ready-made, any other name starts a blank one)
!newchar            make a runner (or !pregen / !join)
!begin              open the first scene - add what kind of run you want: !begin a heist on a Renraku data vault
!help               everything else
```

Just type what your character does. The GM waits for everyone at the table, then answers.

## Tests

`python -m pytest -q` (venv active)

## License

GPL-3.0 - see `LICENSE`.

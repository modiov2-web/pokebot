# pokebot

A minimal, text-only Discord bot for catching the original 151 Pokémon.

> Private repository. Do not share the code, tokens or data without permission.

## Commands

| Command | Text version | What it does |
| --- | --- | --- |
| `/pokemon` | `--pokemon` | A wild Pokémon appears in the channel |
| `/pokeball` | `--pokeball` | Throw a Pokéball to try to catch it |
| `/pokedex` | `--pokedex` | See how many you have caught, plus a few still to find |
| `/caught` | `--caught` | Show up to 5 of the Pokémon you have caught |

## Setup

1. Run `npm install`
2. Copy `.env.example` to `.env` and add your `DISCORD_TOKEN` (and optionally `GUILD_ID`)
3. Run `npm start` (Node 20.6 or newer)

The `--` text commands need **Message Content Intent** switched on in the Developer Portal (Bot tab → Privileged Gateway Intents). Set `GAME_CHANNEL_ID` in `.env` to limit them to one channel. If OSRS chat is relayed into Discord by another bot, set `RELAY_BOT_ID` to that bot's user ID so messages like `Name: --pokemon` are accepted.

Never commit `.env` or `pokedex.json`. They are listed in `.gitignore`.

### Optional: Clan Dex RuneLite plugin

The Clan Dex plugin shows OSRS players their Pokédex in a RuneLite side panel. To feed it, the bot uploads the **in-game players'** catches to a GitHub gist about 15 seconds after each catch, and once at startup.

Names are not published. Each player is listed under a hash of their name made with a clan key (`DEX_SECRET`), so without the key the file is just numbers. Discord-only players are never included.

1. Create a gist at [gist.github.com](https://gist.github.com) with one file named `dex.json` containing `{}`. Make it a **secret** gist.
2. Create a fine-grained token at GitHub → Settings → Developer settings → Personal access tokens, with only **Account permissions → Gists: Read and write**.
3. Pick a clan key: a long random phrase, e.g. from `node -e "console.log(require('crypto').randomBytes(18).toString('base64url'))"`. Share it only with clan members (for example in a members-only Discord channel). They paste it into the plugin's **Clan key** setting.
4. Add all three to `.env`: `GITHUB_TOKEN`, `GIST_ID` (the last part of the gist's URL) and `DEX_SECRET`.
5. Restart the bot. It logs `Clan Dex: published the dex to GitHub`.

Step-by-step instructions, including where everything is in GitHub's settings, are in [CLAN-DEX-SETUP.md](CLAN-DEX-SETUP.md).

The plugin reads `https://gist.githubusercontent.com/<user>/<GIST_ID>/raw/dex.json`. GitHub caches that link for a few minutes, so new catches can take up to about 5 minutes to appear. Leave the keys blank to turn publishing off.

Changing `DEX_SECRET` locks out everyone until they enter the new key. Older revisions of the gist stay readable on GitHub, but they only hold hashes made with the old key.

---

# Terms of Service

Effective date: 07/11/2026

## 1. Who we are and what this is

pokebot (the "Bot") is a text-based Discord bot operated by mark ("we", "us"), based in England. The Bot lets users find and catch Pokémon and keep a personal Pokédex using slash commands. By adding the Bot to a server or using any of its commands, you agree to these Terms. If you do not agree, do not use the Bot.

## 2. Unofficial fan project

The Bot is an unofficial fan project. It is not affiliated with, endorsed by, or sponsored by Nintendo, Creatures Inc., GAME FREAK inc., The Pokémon Company, or Discord Inc. Pokémon and all related names are trademarks of their respective owners. The Bot is free and non-commercial. In Discord it is text only. The optional Clan Dex RuneLite plugin shows the Bot's Pokémon with sprites loaded from the community PokeAPI sprites project. Pokémon names, sprites and artwork are © Nintendo, Creatures Inc. and GAME FREAK inc. They are used here only to refer to and illustrate the game in a non-commercial fan project, and will be removed if the rights holders ask.

## 3. Using the Bot

You must follow Discord's [Terms of Service](https://discord.com/terms) and Community Guidelines, and meet Discord's minimum age requirement. Server owners are responsible for how the Bot is used in their servers. The Bot has no monetary value, and caught Pokémon are not property, cannot be sold, and may be reset or removed at any time.

## 4. Prohibited conduct

You must not, and must not help anyone to:

- attack, overload, or disrupt the Bot or its hosting (including DDoS attacks, command flooding, or deliberate spam);
- gain or try to gain unauthorised access to the Bot, its code, its tokens, its servers, or its stored data;
- exploit bugs, use scripts, self-bots, or automation to cheat, farm catches, or gain an unfair advantage;
- reverse engineer, scrape, or copy the Bot's data or infrastructure in breach of these Terms;
- harass, threaten, or abuse us, our contributors, or other users through the Bot;
- impersonate the Bot or us, or run a copy of the Bot that misleads others;
- use the Bot for anything unlawful.

## 5. Malicious conduct and our right to take legal action

If you deliberately harm, attack, or misuse the Bot (including any conduct listed in section 4), we may, at our sole discretion and without notice:

- block you or any server from using the Bot and delete your Pokédex data;
- report you and your servers to Discord Inc. and to the relevant authorities;
- preserve logs and other evidence of the conduct;
- bring legal proceedings against you to the fullest extent permitted by law, including claims for damages, injunctive relief, and recovery of reasonable costs we incur (such as investigation, repair, hosting, and legal costs); and
- where the conduct amounts to an offence, for example under the Computer Misuse Act 1990, refer the matter to the police.

You agree that serious or repeated malicious conduct may cause us loss that money alone cannot fully repair, and that we may seek urgent court orders to stop it. Nothing in this section limits any other rights or remedies we have under the law.

## 6. Data we keep

We store only what is needed to run the Bot: your Discord user ID and the Pokémon you have caught. We do not sell your data. We may keep temporary logs for security and abuse prevention. To ask for your data to be deleted, contact us using the details below. We handle personal data in line with UK data protection law.

## 7. No guarantees

The Bot is provided "as is" and "as available". We do not promise it will be online, error-free, or that your Pokédex will never be lost or reset. We may change, pause, or shut down the Bot at any time.

## 8. Limit of our liability

To the fullest extent permitted by law, we are not liable for any loss arising from your use of the Bot, including loss of data, caught Pokémon, or Discord server issues. Nothing in these Terms limits liability for death or personal injury caused by negligence, for fraud, or for anything else that cannot legally be limited.

## 9. Changes to these Terms

We may update these Terms from time to time. The effective date above shows the latest version. Continuing to use the Bot after a change means you accept the new Terms.

## 10. Governing law

These Terms are governed by the laws of England and Wales, and the courts of England and Wales have exclusive jurisdiction over any dispute, except that we may seek urgent relief in any court that has jurisdiction over you.

## 11. Contact

Questions, data requests, or reports of abuse: modiov2@gmail.com

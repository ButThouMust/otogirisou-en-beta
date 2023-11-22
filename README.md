# otogirisou-en-beta
(Currently) beta patches for an English translation of Otogirisou for Super Famicom.

**Patches from here are _not_ to be reuploaded to other sites, including but not limited to romhacking.net.**
Note: I mean no ill will against romhacking.net with this. I just don't want the patch to be uploaded/published until it is finished.

# How to patch

You will need an unheadered 1 MB ROM image of the game, which has this specification in the [No-Intro database](https://datomatic.no-intro.org/index.php?page=show_record&s=49&n=1880):
```
Database match: Otogirisou (Japan)
Database: No-Intro: Super Nintendo Entertainment System (v. 20210222-050638)
File/ROM SHA-1: 2C27B89A244ABE941B6A9FCEB1A674DBEFD1F734
File/ROM CRC32: 8E4BEFD0
```

Use any patching utility that supports the BPS format. It should produce a 1.5 MB file. I personally used the utility Floating IPS (available [here](https://www.romhacking.net/utilities/1040/)) to generate the patch.

# How to play the game

Otogirisou is a single player ~~visual~~ sound novel game from Chunsoft (now Spike Chunsoft). It was their debut title as a game publisher, in 1992. The controls are fairly simple:
- A: Confirm menu selection, advance text
- B: Cancel menu selection, advance text
- X: Scroll a page of text back, if available
- Y: Scroll a page of text forward, if you have already scrolled back at least one page
- L: Equivalent to A button
- R: Unused
- Start: Only used on the title screen (advance to menus) and name entry screen (confirm entered name).
- Select: Only used in the name entry menu. It brings you from the grid to the page selector, while preserving your grid position.

You must first name the protagonist (up to 6 characters). He has no default name in the Super Famicom version, but he has a default name of 公平 "Kouhei" in the PlayStation remake of this game. The basic plot is that he and his girlfriend 奈美 "Nami" are driving home from a date, when circumstances force them to take shelter from a rainstorm in a creepy mansion in the middle of nowhere.

The gameplay, so to speak, consists of you reading text and picking a choice from a list when the game presents you with a branching path. This continues until you reach one of several available endings. The game will automatically save your progress whenever you finish a screen of text.

The replayability for this game comes from the different paths you can take. On repeat playthroughs, the game will sometimes present you with new options to pick for choices, which is to say, a choice originally with two options may give you three or even four options.

> [!WARNING]
> If you would like to carry over your save file to the next beta version, you must:
> - [Optional] Finish your playthrough first in whatever version you currently have.
> - Load your save file in the new version, and choose the options `Start` -> `Restart`. This ensures the game is reading text from the proper position in the ROM.
>   - To avoid losing data, I suggest that you have both the older patched game and the newer patched game. Let's say they are `beta_v1.sfc` and `beta_v2.sfc`.
>   - *Make a copy* of your .srm file from, say, `beta_v1.srm` to `beta_v2.srm`.
>   - When you know for sure that your save data has carried over, you can delete the ROM and save data for the old version of the patch.

# Submitting issues

For general suggestions or any issues like bad formatting, please create an issue in this repository, *with a screenshot* of where you found the issue.

Issues in order from most severe to least concern (current priorities in *italics*; list will be added to as needed):
- Game crash or softlock
- Save file deleted
- Irregularities in game behavior (please specify)
- *Translation errors\* and/or poor wording*
- *Too many lines of text that overflow past bottom of screen*
- *Text doesn't auto line break early enough, with a word overflowing past right edge*
- Text auto line breaks too early, when a word can fit in space after break
- Control code mnemonics that slip through as visible text in the script, such as seeing a literal `<LINE 00>` instead of seeing a line break
  - Similar, script comments that begin with `//` that sneak into the game script
- Automatic "wait for player input" triggers too often on punctuation
- Text kerning pairs that should have kerning but don't, or vice versa

\*: In the case of translation errors, please tell me, and we can look at the applicable Japanese text together.

# Known issues
- When presenting the player with a choice, the game recolors the choice option that is currently highlighted. This recoloring may also affect the bottom one or two pixel rows of adjacent choice options (in particular, see the tails of characters like `g`, `j`, or `y`).
  - This is due to how the shortened line leading (distance between lines of text) makes the text align with 8x8 tile boundaries.
  - This is a harmless bug, and currently low priority for fixing.
- The text for one particular ending does not properly trigger the credits (the game effectively softlocks) or mark that ending as viewed for the player's progress. I don't know why this is.

# Checklist of things to do
- Implement an option to enable or disable honorifics
  - TL;DR Nami uses a different one for you each playthrough, so this technically could be considered a game mechanic. Were they not dynamic, I would have just left them out entirely.
  - However, there are several honorifics that are "hard-coded" into the script independent of what Nami uses for you.
- Fill out the font more, add more characters to the name entry screen.
  - Please suggest any characters you'd like to be added, within reason.
- Set more consistent spacing on the file management prompts like `Start`, `Delete`, `Cancel`, `Confirm`, `Resume`, and `Restart`.
- Fix above mentioned choice recoloring issue.

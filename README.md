![title screen](images/01%20title%20screen.png)   ![sample gameplay](images/04%20normal%20text.png)

![file select](images/02%20file%20select.png)    ![name entry](images/03%20name%20entry.png)

# otogirisou-en-beta
(Currently) beta patches for an English translation of Otogirisou for Super Famicom.

**Patches from here are _not_ to be reuploaded to other sites, including but not limited to romhacking.net.**
Note: I mean no ill will against romhacking.net with this. I simply don't want the patch to be uploaded/published anywhere else until it is finished.

# How to patch

You will need an unheadered 1 MB ROM image of the game, which has this specification in the [No-Intro database](https://datomatic.no-intro.org/index.php?page=show_record&s=49&n=1880):
```
CRC32:   8e4befd0
MD5:     ae1e9c92d0b7e6dba6c6007d99c9c3f4
SHA-1:   2c27b89a244abe941b6a9fceb1a674dbefd1f734
SHA-256: d85b6764a35f4dcee3ab5843df1c467ebdfe5f02236043a4e466e6975a3f70ca
```

Use any patching utility that supports the BPS format. It should produce a 1.5 MB file. I personally used the utility Floating IPS (available [here](https://www.romhacking.net/utilities/1040/)) to generate the patch.

# How to play the game

Otogirisou is a single player ~~visual~~ sound novel game from Chunsoft (now Spike Chunsoft). It was both their debut title as a game publisher, in 1992, and the first entry in their sound novel series, which includes games such as Kamaitachi no Yoru, Machi, and 428 Shibuya Scramble. The controls are fairly simple:
- A: Confirm menu selection, advance text
- B: Cancel menu selection, advance text
- X: Scroll a page of text back, if available
- Y: Scroll a page of text forward, if you have already scrolled back at least one page
- L: Equivalent to A button
- R: Unused
- Start: Only used on the title screen (advance to menus) and name entry screen (confirm entered name).
- Select: Only used in the name entry menu. It brings you from the grid to the page selector, while preserving your grid position.

You must first name the protagonist (up to 6 characters). He has no default name in the Super Famicom version but is named 公平 "Kouhei" by default in this game's PlayStation remake.

The basic plot is that he and his girlfriend 奈美 "Nami" are driving home from a date, when circumstances force them to take shelter from a rainstorm in a creepy mansion in the middle of nowhere. It soon becomes apparent that some kind of presence inside clearly doesn't want them there.

The gameplay, so to speak, consists of reading text and picking a choice from a list when the game presents you with a branching path. This continues until you reach one of several available endings. The game will automatically save your progress whenever you finish a screen of text or reach the credits.

The replayability for this game comes from the different paths you can take. Plus, on repeat playthroughs, the game will sometimes present you with new options to pick for choices, which is to say, a choice you first found with two options may give you three or even four options later on.

> [!WARNING]
> If you would like to carry over your save file to the next beta version, you must:
> - [Optional] Finish your playthrough first in whatever version you currently have.
> - Load your save file in the new version, and choose the options `Start` -> `Restart`. This ensures the game is reading text from the proper position in the ROM.
>   - To avoid losing data, I suggest that you have both the older patched game and the newer patched game. Let's say they are `beta_v1.sfc` and `beta_v2.sfc`.
>   - *Make a copy* of your .srm file from, say, `beta_v1.srm` to `beta_v2.srm`.
>   - When you know for sure that your save data has carried over, you can delete the ROM and save data for the old version of the patch.

# Features added for patch
- An English translation I estimate to be 95% complete. **Please let me know if you would like to contribute to the translation!**
  - Translated and restored two screens of text that were unused/inaccessible in the original game.
- A more aesthetically pleasing English font than what was originally in the game.
  - Bypassing of the font compression scheme, to more easily add characters if needed.
  - Linebreaking logic that, while imperfect, is better suited for English text.
  - Text kerning, both horizontally and vertically.
- Translation of all important graphics that contain Japanese text.
  - Title screen, credits, menu text, and one certain graphic in the story.
  - Some graphics do have Japanese text but were kept as-is because the novel text explains them fine.
- Option to let the player enable or disable honorifics.
  - Normally, I would leave them out, but there is an interesting argument for keeping them in. 
  - Nami uses a different one for you on each playthrough, i.e. she may start with san but can switch to kun, chan, etc.
  - Technically, you can classify the dynamic honorifics as a "game mechanic" of sorts.

# Submitting issues

For general suggestions or any issues like bad formatting of game text, please create an issue in this repository, *with a screenshot* of where you found the issue.

Issues in order from most severe to least concern (current priorities in *italics*; list will be added to as needed):
- Game crash or softlock
- Save file deleted
- Irregularities in game behavior (please specify)
- *Translation errors\* and/or poor wording*
- *Too many lines of text that overflow past the bottom of the screen*
- *Text doesn't auto line break early enough, with a word overflowing past the right edge of the screen*
- Text auto line breaks too early, when a word can fit in space after break
- Control code mnemonics that slip through as visible text in the script, such as seeing a literal `<LINE 00>` instead of seeing a line break
  - Similar, script comments that begin with `//` that sneak into the game script
- Automatic "wait for player input" triggers too often on punctuation
- Text kerning pairs that should have kerning but don't, or vice versa

\*: I will eventually release the game script translation for people to consult on their own. There are still a bunch of notes in it like "rewrite this" or "is this translatable?"

# Known issues
- When presenting the player with a choice, the game recolors the choice option that is currently highlighted. This recoloring may also affect the bottom one or two pixel rows of adjacent choice options (in particular, see the tails of characters like `g`, `j`, or `y`).
  - This is due to the shortened line leading (vertical distance between lines of text). While it allows for more text on screen (11 lines vs 9 lines), it makes the text not perfectly align with 8x8 tile boundaries.
  - This is a harmless bug, and currently low priority for fixing.
- Due to how kerning is currently implemented, the one place it does *not* occur is the protagonist's name.
- I have not thoroughly tested the automatic line breaking while accounting for how you can name the protagonist `I`, `WWWWWW`, or something in between.
- The font system technically supports characters that are 15 pixels tall, but Chunsoft seems to have coded parts of the game around how all the characters in their JP font were at most 14 pixels tall, with the vast majority being 13 or shorter.

# Checklist of things to do
- Make a more user-friendly option to enable or disable honorifics.
  - Currently, this works by having two different patches.
  - In the future, I'd like to make it so you can use the otherwise unused R button to enable or disable it.
- Fill out the font more.
  - Please suggest any characters you'd like to be added.
- Set more consistent spacing on the file management prompts like `Start`, `Delete`, `Cancel`, `Confirm`, `Resume`, and `Restart`.
- Fix the above mentioned choice recoloring issue.
- Change the kerning implementation to allow for kerning in the player's name.

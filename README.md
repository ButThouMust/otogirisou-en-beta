![title screen](images/01%20title%20screen.png)   ![sample gameplay](images/04%20normal%20text.png)

![file select](images/02%20file%20select.png)    ![name entry](images/03%20name%20entry.png)

# otogirisou-en-beta
Currently beta patches for an English translation of Otogirisou for Super Famicom. The main bottleneck to a full release is getting the whole script translation peer-reviewed. **Please let me know if you would like to contribute to the translation!** (related [RHDN forum post](https://www.romhacking.net/forum/index.php?topic=38663.0))

**Patches from here are _not_ to be reuploaded to other sites, including but not limited to romhacking.net.** I will upload/submit the patch myself when it is complete, alongside all my notes, tools, etc.

This is a translation project independent of the one by Tom (RetroTranslator) and DDS, for which they released a patch on March 6, 2024.
- I'm still working on mine because I had been working on it for about a year when they announced theirs.
- This is not to dismiss the quality of their project, but please do not send me suggestions for my project based on their project (e.g. "they did X, you did Y, you should change Y to be more like X").

# How to patch

Go to the [releases page](https://github.com/ButThouMust/otogirisou-en-beta/releases) to download the most recent patch version. You will need an unheadered 1 MB ROM image of the game, which has this specification in the [No-Intro database](https://datomatic.no-intro.org/index.php?page=show_record&s=49&n=1880):
```
CRC32:   8e4befd0
MD5:     ae1e9c92d0b7e6dba6c6007d99c9c3f4
SHA-1:   2c27b89a244abe941b6a9fceb1a674dbefd1f734
SHA-256: d85b6764a35f4dcee3ab5843df1c467ebdfe5f02236043a4e466e6975a3f70ca
```

Two patches are included: one for honorifics on, and one for honorifics off (more details about this below). Use whichever patch you prefer, with any patching utility that supports the BPS format. It should produce a 1.5 MB file. I personally used the utility Floating IPS (available [here](https://www.romhacking.net/utilities/1040/)) to generate the patch.

# How to play the game

Otogirisou is a single player sound novel game from Chunsoft (now Spike Chunsoft). It was both their debut title as a game publisher, in 1992, and the first entry in their sound novel series (Kamaitachi no Yoru, Machi, Imabikisou, and 428 Shibuya Scramble).

The controls are fairly simple:
- A: Confirm menu selection, advance text
- B: Cancel menu selection, advance text
- X: Scroll a page of text back, if available
- Y: Scroll a page of text forward, if you have already scrolled back at least one page
- L: Equivalent to A button
- R: Unused
- Start: Only used on the title screen (advance to menus) and name entry screen (confirm entered name).
- Select: Only used in the name entry menu. It brings you from the grid to the page selector, while preserving your grid position.

You must first name the protagonist (up to 6 characters). He has no default name in the Super Famicom version but is named 公平 "Kouhei" by default in this game's PlayStation remake. The basic plot is that Kouhei and his girlfriend 奈美 "Nami" are driving home from a date, when circumstances force them to take shelter from a rainstorm in a creepy mansion. It soon becomes apparent that some kind of presence inside clearly doesn't want them there.

The gameplay, so to speak, consists of reading text and picking a choice from a list when the game presents you with a branching path. This continues until you reach one of several available endings. The game will automatically save your progress whenever you finish a screen of text or reach the credits.

The replayability for this game comes from the different paths you can take, as well as the different endings you can view. Plus, on repeat playthroughs, the game will sometimes present you with new options to pick for choices, which is to say, a choice you first found with two options may give you three or even four options later on.

> [!WARNING]
> If you would like to carry over your save file to the next beta version, you must:
> - [Optional] Finish your playthrough first in whatever version you currently have.
> - Load your save file in the new version, and choose the options `Start` -> `Restart`. This ensures the game is reading text from the proper position in the ROM.
>   - To avoid losing data, I suggest that you have both the older patched game and the newer patched game. Let's say they are `beta_v1.sfc` and `beta_v2.sfc`.
>   - *Make a copy* of your .srm file from, say, `beta_v1.srm` to `beta_v2.srm`.
>   - When you know for sure that your save data has carried over, you can delete the ROM and save data for the old version of the patch.

# Features added for patch
- An English translation I estimate to be 95% complete.
  - Translated and restored two screens of text that were unused/inaccessible in the original game.
- A more aesthetically pleasing English font than what was originally in the game.
  - Bypassing of the font compression scheme, to more easily add/edit characters if needed.
  - Linebreaking logic that, while imperfect, is better suited for English text.
  - Text kerning, both horizontally and vertically.
- Translation of all important graphics that contain Japanese text.
  - Title screen, credits, menu text, and one certain graphic in the story.
  - There are a few graphics where their Japanese text was left alone because the novel text explains them fine.
- Option to let the player enable or disable honorifics.
  - Normally, I would have left them out altogether, but there is an interesting argument for keeping them in. 
  - The original Japanese game has a "game mechanic" where Nami uses a different honorific for you on each playthrough. For example, she may start with san but can switch to kun, chan, etc.
  - If you want to see them when playing, great! However, I programmed this feature because I do recognize that some people prefer to leave them out.

# Submitting issues

For general suggestions or any issues like bad formatting of game text, please contact me *with a screenshot* of where you found the issue. You can create an issue here, reply to the [RHDN forum post](https://www.romhacking.net/forum/index.php?topic=38663.0) I made for this project, or join the [RHDN Discord](https://discord.gg/uAufcgz) and contact me there.

Issues in order from most severe to least concern (current priorities in *italics*; list will be added to as needed):
- Game crash or softlock
- Save file deleted
- Irregularities in game behavior (please specify)
- *Translation errors\* and/or poor wording*
- *Too many lines of text that overflow past the bottom of the screen*
- *Text doesn't auto line break early enough, with a word overflowing past the right edge of the screen*
- Text auto line breaks too early, when a word can fit in space after break
- Control code mnemonics that slip through as visible text in the script
  - For example, seeing a literal `<LINE 00>` instead of seeing a line break
  - Similar, script comments that begin with `//` that sneak into the game script
- Automatic "wait for player input" triggers too often on punctuation
- Text kerning pairs that should have kerning but don't, or vice versa

\*: I will eventually release the game script translation for people to consult on their own. There are still a bunch of notes in it like "rewrite this" or "is this translatable?"

# Known issues
- Due to how kerning is currently implemented, the one place it does *not* occur is the protagonist's name.
- I have not thoroughly tested the automatic line breaking while accounting for how you can name the protagonist `I`, `WWWWWW`, or something in between.

# Checklist of things to do
- Make a more user-friendly option to enable or disable honorifics.
  - Currently, this works by having two different patches. So if you want to switch, you would have to keep two patched copies and rename your save data accordingly.
  - In the future, I'd like to make it so you can use the otherwise unused R button to enable or disable it.
- Change the kerning implementation to allow for kerning in the player's name.
- (Low priority) Set more consistent spacing on the file management prompts like `Start`, `Delete`, `Cancel`, `Confirm`, `Resume`, and `Restart`.

# Project credits
Alphabetical list of people who have contributed to this project, directly or indirectly, at some point:
- ["Guest"](https://www.romhacking.net/community/695/): Creator of original tools (script/font dumpers) and notes in abandoned project "starter pack" on RHDN
- Karu: Translation assistance
- [Koitsu](https://www.romhacking.net/community/394/): Provided notes on game's font compression format and its VWF implementation
- Lazermutt4: Translated two of the game's graphics, and pointed me to the font that I would use for the end credits
- MLagaffe: Provided font for main text; suggested ideas for assembly hacks related to in-game text formatting
- Squeaky: Translation assistance

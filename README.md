# SwiftKey → HeliBoard Migration Guide

> **⚠️ Deadline: May 31, 2026** — SwiftKey account data will be permanently deleted after this date. Export your data before then.

A complete, ADB-free guide to migrate your SwiftKey learned vocabulary and settings to [HeliBoard](https://github.com/Helium314/HeliBoard), a privacy-focused, open-source Android keyboard.

---

## Table of Contents

[Why HeliBoard?](#why-heliboard)

1. [Export Your SwiftKey Data](#1-export-your-swiftkey-data)
2. [Convert the Dictionary](#2-convert-the-dictionary)
3. [Install HeliBoard](#3-install-heliboard)
4. [Import Your Dictionary](#4-import-your-dictionary)
5. [Configure HeliBoard like SwiftKey](#5-configure-heliboard-like-swiftkey)
6. [Back Up HeliBoard Settings](#6-back-up-heliboard-settings)
7. [Uninstalling UDM](#7-uninstalling-udm)
8. [What Doesn't Transfer](#8-what-doesnt-transfer)

---

## Why HeliBoard?

SwiftKey's forced migration to Microsoft accounts is a good opportunity to rethink which keyboard you trust with everything you type. Here's why HeliBoard is a strong choice.

### 🔒 Zero Network Access — By Design

HeliBoard **does not request internet permission** at all. This means everything you type stays on your device — no keystrokes, learned words, or personal data ever leave your phone. SwiftKey and Gboard both send typing data to cloud servers for prediction improvements. HeliBoard's predictions run entirely offline.

### 🆓 Free, Open Source, No Ads

HeliBoard is fully open source (Apache 2.0 license), has no ads, no subscriptions, and no telemetry. The source code is publicly auditable on [GitHub](https://github.com/Helium314/HeliBoard), which means the privacy claims can actually be verified — unlike closed-source alternatives.

### ⚙️ More Customizable Than Gboard or SwiftKey

HeliBoard matches or exceeds both Gboard and SwiftKey in features:

- Unlimited clipboard history (Gboard caps at 5 items and resets hourly)
- Fully customizable toolbar icons
- Custom key height, padding, and layout
- Material You dynamic theming + custom background images
- Forced incognito mode (disables learning for sensitive contexts)
- Custom layouts and key overrides per language

### 🌍 Solid Multilingual Support

You can type in multiple languages simultaneously without manually switching — HeliBoard detects the language mid-sentence. Dictionaries are downloaded locally per language and work fully offline.

### 🛠️ Actively Maintained

HeliBoard is based on AOSP/OpenBoard and actively maintained by the community on GitHub. Bug reports and feature requests are handled publicly and transparently.

### ⚖️ Honest Limitations

HeliBoard is not perfect:

- **Predictive text** is good but not yet on par with SwiftKey's neural model — it will improve as it learns your patterns
- **Swipe/gesture typing** requires a separate library download (closed-source, optional)
- **Setup takes a few minutes** — it doesn't come pre-configured out of the box like Gboard
- **Updates are less frequent** than commercial keyboards

For most users coming from SwiftKey, the trade-off is clear: you lose a slightly smarter autocorrect cloud model, and you gain complete privacy, no account requirements, and no risk of future forced migrations.

### 📊 Comparison: HeliBoard vs FUTO Keyboard

| Criterion | HeliBoard | FUTO Keyboard |
|---|---|---|
| **License** | Open source — Apache 2.0  [github](https://github.com/HeliBorg/HeliBoard) | Open source — public code on GitHub  [cybersecuritythreatai](https://cybersecuritythreatai.com/futo-keyboard-fortifying-your-mobile-privacy-against-ai-powered-data-leaks-and-keyboard-tracking-threats/) |
| **Internet Access** | ❌ None  [discuss.privacyguides](https://discuss.privacyguides.net/t/heliboard-offline-keyboard-for-android/28093) | ❌ None  [cybersecuritythreatai](https://cybersecuritythreatai.com/futo-keyboard-fortifying-your-mobile-privacy-against-ai-powered-data-leaks-and-keyboard-tracking-threats/) |
| **Swipe Typing** | ✅ Via external downloadable library  [forum.f-droid](https://forum.f-droid.org/t/heliboard-the-best-gboard-alternative/32634) | ✅ Natively integrated (alpha)  [thecadmasters](https://thecadmasters.com/futo-keyboard-secure-offline-typing-for-the-privacy-conscious/) |
| **Offline Voice Input** | ❌ Not included | ✅ Natively included, downloadable models  [windowsforum](https://windowsforum.com/threads/futo-keyboard-the-offline-first-android-keyboard-for-true-on-device-privacy.405419/) |
| **Autocorrect Quality** | ⭐⭐⭐ Good, improves with usage  [reddit](https://www.reddit.com/r/privacy/comments/1lksnc5/fossify_or_futo_keyboard/) | ⭐⭐⭐⭐ Superior according to user feedback  [lemmy.dbzer0](https://lemmy.dbzer0.com/post/35503843) |
| **Multilingual Support** | ✅ Excellent — automatic mid-sentence detection  [github](https://github.com/Helium314/HeliBoard/discussions/550) | ⚠️ Limited, less mature  [reddit](https://www.reddit.com/r/foss/comments/1n3c0q0/heliboard_vs_futo_keyboard/) |
| **Customization** | ⭐⭐⭐⭐⭐ Very advanced — height, themes, toolbar, layouts  [discuss.privacyguides](https://discuss.privacyguides.net/t/heliboard-offline-keyboard-for-android/28093) | ⭐⭐ Basic — themes in development  [lemmy.dbzer0](https://lemmy.dbzer0.com/post/35503843) |
| **Maturity / Stability** | ✅ Stable, v2.x+ | ⚠️ Still in alpha/beta  [forum.f-droid](https://forum.f-droid.org/t/heliboard-the-best-gboard-alternative/32634) |
| **Availability** | F-Droid, GitHub, Play Store | F-Droid, Play Store, Direct APK  [cybersecuritythreatai](https://cybersecuritythreatai.com/futo-keyboard-fortifying-your-mobile-privacy-against-ai-powered-data-leaks-and-keyboard-tracking-threats/) |
| **Migration from SwiftKey** | ✅ Via this guide | ❌ No documented procedure |

---

## 1. Export Your SwiftKey Data

SwiftKey does not allow a local export — you must go through its web portal, which requires a Microsoft account.

**If you already have a Microsoft account**, skip to step 4 below.

**If you don't have a Microsoft account:**

1. Create a **temporary Microsoft account** at [account.microsoft.com](https://account.microsoft.com)
   - You can use a disposable email address (e.g. [temp-mail.org](https://temp-mail.org))
2. In SwiftKey → **Settings → Account → Sign In** with that account
3. Wait a few seconds for the sync to complete

**Export steps (all users):**

4. On a PC, go to [data.swiftkey.com](https://data.swiftkey.com) and sign in
5. Click **View Data → Export All**
6. Download the ZIP file — it will be named `userdata-{your-id}-{date}.zip`
7. Extract the ZIP — you will find:
   - `demographics.json` ← ignore this
   - `services/sync_words.json` ← **this is your dictionary**
8. Copy `sync_words.json` to the folder where you will run the converter script

> You may delete the temporary Microsoft account afterwards if you created one for this purpose.

---

## 2. Convert the Dictionary

HeliBoard cannot directly import SwiftKey's JSON format. The raw data also contains noise (URLs, email addresses, numbers, timestamps) that would pollute your dictionary. The script below cleans and converts it.

**Requirements:** Python 3 installed on your PC ([python.org](https://python.org))

Save the following as `convert.py` in the same folder as `sync_words.json`:

```python
import json, re

with open("sync_words.json", encoding="utf-8") as f:
    data = json.load(f)

terms = data.get("terms", [])

def is_valid_word(w):
    if len(w) < 2 or len(w) > 50:
        return False
    if re.search(r'\d', w):           # remove anything with digits
        return False
    if re.search(r'[@/:\.\\]', w):    # remove emails, URLs, paths
        return False
    if not re.search(r'[a-zA-ZÀ-ÿ]', w):  # must contain at least one letter
        return False
    return True

cleaned = sorted(set(filter(is_valid_word, terms)))

with open("heliboard_wordlist.txt", "w", encoding="utf-8") as f:
    f.write("\n".join(cleaned))

print(f"Done: {len(cleaned)} words exported out of {len(terms)} total terms.")
```

Run it:

```bash
python convert.py
```

This produces `heliboard_wordlist.txt` — a plain text word list ready for import.

---

## 3. Install HeliBoard

Install HeliBoard from one of these sources:

- [F-Droid](https://f-droid.org/packages/helium314.keyboard/) *(recommended — no Google)*
- [GitHub Releases](https://github.com/Helium314/HeliBoard/releases)

Then enable it as your default keyboard:

1. **Android Settings → System → Language & Input → On-screen keyboard → Manage keyboards** → enable HeliBoard
2. Tap **Select keyboard** in any text field → choose HeliBoard

---

## 4. Import Your Dictionary

[UDM (User Dictionary Manager)](https://play.google.com/store/apps/details?id=com.dooboolab.UDM) is required as a bridge to inject words into Android's system dictionary, which HeliBoard reads.

1. Install **UDM** from F-Droid or the Play Store
2. Copy `heliboard_wordlist.txt` to your phone
3. Open UDM → **Import**
4. Select format: **Plain Text / Word List** *(not Gboard/CSV)*
5. Select your file
6. Assign language: `fr_FR`, `en_US`, or **All languages** depending on your use case
7. Tap **Start**

**Verify the import:**

Go to **HeliBoard Settings → Dictionary → Personal Dictionary** — you should see your words listed there.

---

## 5. Configure HeliBoard like SwiftKey

### 5.1 Multilingual Typing (e.g. French + English simultaneously)

> ⚠️ You must tap the **language name** — not the toggle switch — to access multilingual options.

1. **Settings → Languages & Layouts** → tap **+ Add Language** → select `French (fr_FR)`
2. Tap the **French language name** → tap **+** next to *Multilingual typing* → add `English (en_US)`
3. **Settings → Dictionary → Add dictionary** → download dictionaries for both `fr_FR` and `en_US`

### 5.2 Suggestion Strip (3-word bar with space = validate middle word)

In **Settings → Text Correction**, enable the following:

| Setting | Value |
|---|---|
| Show suggestions | ✅ Enabled |
| Always show middle suggestion | ✅ Enabled |
| Automatically replace with middle suggestion | ✅ Enabled |
| Auto-correction | *Modest* (adjust to taste) |
| Next-word suggestions | ✅ Enabled |

> The middle word appears **bold** when it differs from what you typed (i.e. autocorrect will trigger on space). If not bold, pressing space keeps your typed word as-is.

### 5.3 Swipe/Glide Typing (optional)

HeliBoard does not bundle the gesture library due to licensing restrictions. To enable it:

1. Download `gesture_typing_library.zip` from the [HeliBoard GitHub releases page](https://github.com/Helium314/HeliBoard/releases)
2. Extract the `.so` file matching your CPU architecture (usually `arm64-v8a`)
3. In HeliBoard: **Settings → Advanced → Load Gesture Typing Library** → select the `.so` file

### 5.4 Comfort & Layout Settings

| Feature | Path |
|---|---|
| Number row | Settings → Preferences → Number row ✅ |
| Double-space adds period | Settings → Typing → Double-space period ✅ |
| Swipe spacebar to switch language | Settings → Advanced → Horizontal spacebar swipe → *Switch language* |
| Key height / padding | Settings → Appearance → Custom key height |
| Theme (Material You) | Settings → Appearance → Theme → *Material You* |

### 5.5 Toolbar Customization

**Settings → Appearance → Customize toolbar icons** — recommended icons to add:

- Clipboard
- Undo / Redo
- Select word
- Voice input *(optional)*

### 5.6 Fix for Reddit and Google Keep (No Suggestions Bug)

This bug is well known and has a specific cause: the Reddit app (and some others) sets a `TYPE_TEXT_FLAG_NO_SUGGESTIONS` flag on its text fields. HeliBoard respects this flag by default — unlike SwiftKey or Gboard which ignore it.

The fix in a single step:

**HeliBoard Settings → Text Correction → Always show suggestions** → ✅ Enable

Also verify that this option is disabled:

**Text Correction → Don't show suggestions for web edit fields** → ❌ Disable

That's it. Suggestions will now appear in Reddit, Google Keep, and all other fields using this flag.

---

## 6. Back Up HeliBoard Settings

Once everything is configured, back up your settings so you never have to redo this:

**HeliBoard Settings → Advanced → Back up settings** → save the file in a safe location.

To restore on a new device: **Settings → Advanced → Restore settings** → select the backup file.

---

## 7. Uninstalling UDM

**Yes, you can uninstall UDM immediately** after the import. UDM is only a transfer tool. Once words are injected into Android's system personal dictionary, they belong to HeliBoard and UDM plays no further role.

---

## 8. What Doesn't Transfer

| SwiftKey Feature | Status |
|---|---|
| Learned autocorrect model / AI predictions | ❌ HeliBoard will re-learn from scratch |
| Themes | ❌ Must be reconfigured manually |
| Clipboard history | ❌ Not exported by SwiftKey |
| Personal dictionary (manually added words) | ✅ Transferred via this guide |
| Learned vocabulary (typed words) | ✅ Transferred via this guide |

---

## Credits & References

- [SwiftKey Data Portal](https://data.swiftkey.com)
- [HeliBoard GitHub](https://github.com/Helium314/HeliBoard)
- [User Dictionary Manager (UDM)](https://play.google.com/store/apps/details?id=com.dooboolab.UDM)
- Original dictionary converter concept: [AiCurv/SwiftKey-to-HeliBoard (GitHub Gist)](https://gist.github.com/AiCurv/dc16a89ffe09c0d25f24049dcff40005)

---

*Guide written in March 2026. Tested on Android 13/14. SwiftKey account retirement deadline: May 31, 2026.*

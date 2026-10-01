# Village Run: Google Play launch guide

Everything Google Play asks for, with the answer for this app. Work top to bottom. Requirements checked on 1 October 2026.

## 1. Requirements check

| Google Play requirement | Status for Village Run |
|---|---|
| Target Android 16 (API 36) for new apps since 31 Aug 2026 | Done. targetSdk and compileSdk are 36 |
| Upload as an Android App Bundle (.aab), signed with an upload key | Done. The GitHub workflow builds a signed .aab; the upload key is in your private folder |
| 64-bit and 16 KB memory page support | Done. The app has no native (C/C++) code of its own; Capacitor 8 ships compliant libraries |
| Edge-to-edge display (enforced from Android 15) | Done. Full-screen game; notch and gesture-bar insets keep buttons clear |
| Privacy policy at a public URL, also reachable in the app | Done. `docs/privacy-policy.html` to host, plus a **Privacy** link on the game menu |
| Families policy (all ages, including children) | Done. No ads, no analytics, no SDKs, no personal data, no external links |
| Data safety form | Answers below: no data collected or shared |
| Content rating (IARC questionnaire) | Answers below |
| App icon 512×512, feature graphic 1024×500, at least 2 phone screenshots | Done. In the `store-assets` folder: 1 icon, 1 feature graphic, 8 screenshots at 1080×1920 |
| Short description of 80 characters or fewer | Done. 76 characters |
| Android back button behaves sensibly | Done. Pauses the run → quits to menu → closes the app |
| Pauses when the app goes to the background | Done. Game pauses, sound stops, progress is saved |
| Closed test: 12 testers for 14 days (personal accounts created after 13 Nov 2023) | You do this. Plan in step 5 |

## 2. Create your developer account

1. Go to play.google.com/console and sign up as a **personal** developer. There is a one-time US$25 fee.
2. Complete identity verification (government ID) and verify a phone number and email. This can take a few days.
3. The developer name you choose is shown publicly under the app.

## 3. Build the app bundle

Follow `README.md` → "Build the signed app bundle on GitHub". Add the four secrets, run the workflow, and download `village-run-release-aab`.

Keep the private folder (`village-run-upload.jks`, its password and the base64 copy) somewhere safe and off GitHub: a password manager plus an offline copy. If you lose it, Google can reset the upload key from Play Console, but that takes a few days.

## 4. Create the app in Play Console

**Create app**

| Field | Value |
|---|---|
| App name | Village Run: Bharat Yatra |
| Default language | English (India), en-IN |
| App or game | Game |
| Free or paid | Free |
| Declarations | Tick both (Developer Program Policies, US export laws) |

**App signing.** When you upload the first .aab, accept **Play App Signing**. Google then holds the app signing key, and your upload key only proves uploads are yours.

For reference, your upload certificate fingerprints:

- SHA-1: `59:3A:58:85:83:C3:DB:83:D0:27:6D:81:DA:A6:42:04:A1:C9:D6:33`
- SHA-256: `5F:D8:74:B2:52:C1:92:CD:22:86:C0:BC:C0:E8:64:FE:A9:C5:5C:27:44:12:69:66:37:B8:3F:E4:89:F7:31:9A`

## 5. Closed testing (required before production)

1. **Testing → Closed testing → Create track.** Upload the .aab and add release notes (text below).
2. **Testers:** create an email list with **at least 12 people** (aim for 15–20 so dropouts don't sink you). Each must have an Android phone and opt in through the test link.
3. Testers must stay opted in **for 14 days in a row**. Anyone who leaves and rejoins restarts their 14 days. Ask them to actually play a few times.
4. Fix anything they report and upload new builds to the same track (each GitHub run raises the versionCode automatically).
5. After 14 days, go to **Dashboard → Apply for production**. Google asks about your testing. Answer honestly in your own words, covering:
   - who tested (friends, classmates, family)
   - how many testers
   - what they tried (all four laps, unlocking runners, the tasla, revive)
   - what feedback you received and what you changed
   - why the app is ready
6. Google usually replies within 7 days.

## 6. App content (Policy → App content)

**Privacy policy.** Host `docs/privacy-policy.html` publicly (see README → "Privacy policy hosting") and paste its URL.

**Ads.** No, my app does not contain ads.

**App access.** All functionality is available without special access (no login).

**Content rating.** Start the IARC questionnaire:

| Question | Answer |
|---|---|
| Category | Game |
| Violence | No. A cartoon dog chases the runner; nobody is hurt or shown injured |
| Fear or horror | No |
| Sexuality or nudity | No |
| Language | No |
| Controlled substances | No depiction of use, sale or encouragement. See note |
| Gambling | No (no betting, no real-money or simulated casino games) |
| Users interact or exchange information | No |
| Shares location | No |
| Digital purchases | No |
| Unrestricted internet | No |

The expected result is the lowest rating band (for example, PEGI 3 / Everyone / IARC 3+).

**Note on the "Ghazipur Opium Factory" landmark.** It is a real historical government factory, shown only as a building with a name board. It does not depict, mention or encourage drug use, so answer "No" to drug use questions. If the questionnaire asks specifically whether the app *references* drugs by name and you want to be extra careful for a children's audience, rename the board to "Ghazipur Alkaloid Works" before submitting.

**Target audience and content**

| Field | Value |
|---|---|
| Target age groups | Ages 5 & under, 6–8, 9–12, 13–15, 16–17, 18 and over |
| Appeals to children | Yes |
| Store listing shown to children | Yes |
| Families policy | Confirm compliance. The app has no ads, no third-party SDKs, collects no data and has no external links |

Optionally, opt into the "Teacher Approved" programme later.

**Data safety**

| Question | Answer |
|---|---|
| Does your app collect or share any of the required user data types? | No |
| Is all user data encrypted in transit? | Not applicable (no data is transmitted) |
| Do you provide a way for users to request deletion? | Not applicable (no data is collected) |

Result: "No data collected · No data shared". Progress saved only on the phone does not count as collection.

**Government apps:** No. **Financial features:** None. **Health apps:** No. **News app:** No.

## 7. Store listing (Grow → Store presence → Main store listing)

**App name** (30 max): Village Run: Bharat Yatra

**Short description** (80 max, this is 76):
Run through 24 Indian cities, dodge cows and carts, and outrun Moti the dog!

**Full description:**

Moti the street dog wants your laddoos, and the race is on!

Run along winding village paths across India, from Amritsar to Alappuzha. Every city has its own season, people, rivers and famous monuments: the Golden Temple, the Taj Mahal, the ghats of Varanasi at night, Rumi Darwaza, Howrah Bridge, Hawa Mahal, Charminar, Mysore Palace, the backwaters of Kerala and many more.

HOW TO PLAY
• Swipe left or right to switch lanes
• Swipe up to jump over hay bales, logs, pots and potholes
• Swipe down to slide under clotheslines and marigold garlands
• Dodge cows, bullock carts, tractors, camels and auto-rickshaws
• Double-tap to hop on a tasla and glide over trouble

24 CITIES, 4 LAPS
Each city lasts 500 metres and every 6 cities is a lap. Finish a lap to win laddoos and keys, and the reward doubles every lap, up to 4,000 laddoos and 40 keys for completing the full Bharat Yatra.

24 RUNNERS FROM ACROSS INDIA
Pick a kid from every city, each in local dress, and start the run in their home town. Unlock more runners and costumes (Festival, Winter, Cricket kit) with the laddoos and keys you collect.

POWER-UPS AND REVIVES
Grab magnets, shields and 2x score. Use keys to revive after a crash, and claim a free key every day.

• Works fully offline
• No ads, no in-app purchases, no data collection
• Suitable for the whole family

**Graphics** (from `store-assets`)

| Asset | File |
|---|---|
| App icon | `icon-512.png` |
| Feature graphic | `feature-graphic-1024x500.png` |
| Phone screenshots | All 8 PNGs in `screenshots/`, in numbered order |

**Category and contact**

| Field | Value |
|---|---|
| Category | Game → Arcade |
| Tags | Runner, Casual, Offline (pick what the console offers) |
| Email | sharadsingh0203@gmail.com (shown publicly; use a separate address if you prefer) |
| Website | Optional |
| Privacy policy | Same URL as in App content |

**Release notes for 1.0.0:**
First release: run across 24 Indian cities in 4 laps, 24 runners with costumes, tasla rides, lap rewards and daily free keys.

## 8. Production release

After production access is granted:

1. **Production → Create release.** Promote the tested build or upload the latest .aab.
2. **Countries:** India, plus any others you want.
3. Review, then **Start rollout**.

Google's review of the first release can take a few days.

## 9. Before every update

- Change the game in `www/index.html`, run `npx cap sync android`, raise `versionName` in `android/app/build.gradle`, commit and run the workflow.
- Keep the target SDK current. Google raises the minimum each August.

## Sources

- Target API level requirements: https://support.google.com/googleplay/android-developer/answer/11926878
- Testing requirements for new personal accounts: https://support.google.com/googleplay/android-developer/answer/14151465
- Families policy: https://support.google.com/googleplay/android-developer/answer/9893335
- Store listing graphics: https://support.google.com/googleplay/android-developer/answer/9866151
- 16 KB page sizes: https://developer.android.com/guide/practices/page-sizes

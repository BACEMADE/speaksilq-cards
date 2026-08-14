# Speak Silq — Pastel Graphics Library

517 vocabulary cards, 5,792 word pairs, 5 languages. All regenerated in the 20-colour
pastel palette, 4:5 (2160 × 2700 px), PNG.

---

## 1. Folder structure

```
SpeakSilq_Pastel_Graphics/
├── 01_pashto/            92 cards   ← in rotation
├── 02_farsi/            118 cards   ← in rotation
├── 03_dari/              92 cards   ← in rotation
├── 04_urdu/              76 cards   ← in rotation
├── 05_bengali/          104 cards   ← in rotation
├── 06_pashto-sampler/    33 cards   ← NOT in rotation (see §5)
├── 07_extras/             2 cards   ← NOT in rotation (see §5)
└── _index/
    ├── master_index.csv          every card + caption + alt text + hashtags
    ├── posting_schedule_ALL.csv  all 482 scheduled posts, chronological
    ├── posting_schedule_<lang>.csv  one file per account
    ├── content_database.json     every card's full word list
    └── README.md                 this file
```

Each language keeps its own folder. Nothing is mixed between languages.

---

## 2. The naming convention

```
pashto_14-food-drink_p2of4_food.png
└─┬──┘ └┬┘└────┬────┘ └──┬──┘ └─┬┘
  │     │      │         │      └── theme family (anti-clustering key)
  │     │      │         └───────── part 2 of 4 in this category
  │     │      └─────────────────── category, human readable
  │     └────────────────────────── category code 01–35, fixed across ALL languages
  └──────────────────────────────── language / account
```

Read left to right, the filename answers every question you need before posting:
**which account, where it sits in the curriculum, what it's about, which part it is,
and which theme it belongs to.** No lookup required.

Two properties worth knowing:

- **The category code is global.** `14` is Food & Drink in Pashto, Farsi, Dari, Urdu
  and Bengali alike. Sorting any folder alphabetically gives you curriculum order.
- **`p2of4` is explicit about the total.** You can see at a glance that three siblings
  exist elsewhere in the folder, without counting files.

### Category codes

| # | Category | Theme |
|---|---|---|
| 01 | greetings-courtesy | social |
| 02 | everyday-phrases | social |
| 03 | question-words | social |
| 04 | people-pronouns | social |
| 05 | connectors-prepositions | social |
| 06 | numbers | time |
| 07 | time-frequency | time |
| 08 | days-months-seasons | time |
| 09 | daily-routine | time |
| 10 | family-relationships | people |
| 11 | emotions-feelings | people |
| 12 | body-parts | people |
| 13 | health-medical | people |
| 14 | food-drink | food |
| 15 | fruits-vegetables | food |
| 16 | cooking-kitchen | food |
| 17 | restaurant-ordering | food |
| 18 | home-household | home |
| 19 | clothing-accessories | home |
| 20 | shopping-money | home |
| 21 | colours | home |
| 22 | travel-transport | travel |
| 23 | directions-places | travel |
| 24 | city-places | travel |
| 25 | hotel-accommodation | travel |
| 26 | nature-weather | world |
| 27 | animals-birds | world |
| 28 | emergencies-safety | world |
| 29 | common-verbs | learn |
| 30 | adjectives-opposites | learn |
| 31 | work-professions | learn |
| 32 | education-school | learn |
| 33 | technology-communication | learn |
| 34 | sports-leisure | learn |
| 35 | religion-culture | learn |

Category names vary slightly between languages (Farsi says *Greetings & Politeness*,
Urdu says *Greetings & Courtesy*). Both map to code `01`, so the code — not the wording —
is what you match on.

### The 8 theme families

`social` · `time` · `people` · `food` · `home` · `travel` · `world` · `learn`

The theme is the anti-clustering key. Two cards from the same theme should never post
back-to-back, even if they're from different categories — otherwise the feed reads as
three days of food, then three days of travel.

---

## 3. The posting schedule

**Frequency:** 2 posts per day per account, at **01:00** and **13:00** America/Los_Angeles.
The schedule starts **Monday 17 August 2026** and runs to the length of each account's library:

| Account | Cards | Days | Ends |
|---|---|---|---|
| speaksilq_farsi | 118 | 59 | 14 Oct 2026 |
| speaksilq_bengali | 104 | 52 | 07 Oct 2026 |
| speaksilq_pashto | 92 | 46 | 01 Oct 2026 |
| speaksilq_dari | 92 | 46 | 01 Oct 2026 |
| speaksilq_urdu | 76 | 38 | 23 Sep 2026 |

To feed PostHog, use `posting_schedule_ALL.csv` (or one per account). Columns:

`post_at_local, post_date, post_time, account, language, file_path, filename, category,
theme, part, parts, palette, caption, alt_text, hashtags`

`file_path` is relative to `SpeakSilq_Pastel_Graphics/`, so it resolves wherever you host the folder.

### Guarantees the ordering satisfies

Verified programmatically across all 5 accounts:

| Rule | Result |
|---|---|
| Two parts of the same category never post back-to-back | **0 violations** |
| Two cards of the same theme never post back-to-back | **0 violations** |
| Minimum gap between parts of one category | **6–12 posts (3–6 days)** |
| Median gap between parts of one category | **17–25 posts (8–12 days)** |
| Background colour never repeats on consecutive posts | **0 violations** |
| More than 2 accounts posting the same theme in the same slot | **0 of 118 slots** |

So part 1 of *Food & Drink* posts on a Tuesday morning, part 2 lands roughly a week later,
and nothing else food-related runs on either side of them. Across accounts, the 01:00 slot
never turns into "everybody posts greetings at once."

---

## 4. The palette

20 pastels, assigned by schedule position using a stride of 7 across the palette (0, 7, 14, 1, 8, 15 …).
The stride matters: assigning them in listed order would walk the hue wheel slowly and give you a
week of pinks, then a week of yellows. Stepping by 7 jumps across the wheel, so consecutive posts
not only differ, they contrast — and no colour repeats within any 6-post window. Every card's exact colours are in `master_index.csv`
(`palette`, `background_hex`, `accent_hex`).

- **Background** — one of the 20 pastels, flat, no pattern.
- **English column** — `#2E2B31` deep neutral, ≥10:1 contrast on every pastel.
- **Romanised column + subtitle + icon** — a deepened version of that card's own pastel,
  ≥5:1 contrast on its background. Same hue family, so each card reads as one colour story.

---

## 5. What is deliberately NOT in the posting rotation

**`06_pashto-sampler/` (33 cards)** — these came from `round1_all33_categories`, which was
one sample card per category pulled from a larger Pashto set. Their vocabulary already
appears in `01_pashto/`. They're regenerated and available, but scheduling them would post
the same words to the same account twice. Use them for ads, carousels, or a second Pashto
channel — not the main queue.

**`07_extras/` (2 cards)** — one Farsi and one Pashto card that were the last survivors of
two folders (`Farsi Graphics`, `speaksilq_pashto_graphics_full141`) that disappeared from
the source directory mid-run. Their content is covered by the main sets.

---

## 6. Adding a new language later

1. Create `0N_<language>/`.
2. Name files `<language>_<NN>-<category-slug>_p<k>of<n>_<theme>.png` using the codes in §2.
3. Append rows to `master_index.csv` and generate a schedule with the same two rules:
   no same category and no same theme back-to-back.

The convention carries over unchanged — that's the point of the fixed category codes.

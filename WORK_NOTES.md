# Work Notes (Claude session memory)

Rules for this file:
- Only things that were actually done and checked go under **Done**.
- Anything guessed or estimated is marked **ASSUMED**.
- Anything not done is listed under **Not done / open**.
- Files under `/tmp/claude-0/...` (scratchpad) are temporary and get wiped when the session container is reclaimed. Only this repo file survives, and only if it is committed and pushed.

Last updated: 2026-11-24

---

## 1. Orbis Corporate Solutions website (orbiscorpsol.com)

**Host:** Netlify site `orbis-corporate-review`. User has no laptop, so edits were made and deployed from here.

**Done (deployed and checked with before/after screenshots):**
- All 14 items from the user's PDF change note applied:
  - City labels
  - Sidebar scroll
  - Trademark line
  - UAE phone
  - India address and phone
  - Careers "Work with Orbis" card
  - Terms and Disclaimer text
  - Draft banners
  - Cookie Policy
  - India hero image
- Locations banner: India strip replaced with the Mumbai skyline; Statue of Liberty added to the USA strip.
- `noindex` removed.
- Consultation form uses Web3Forms access key `51b6612e-17b0-4854-a482-322026b1e8a8` (the user supplied it).
- Disclaimer popup fixed for phones.
- "Powered by Netlify" badge: it appeared after the first deploy; the hide style was restored and the site redeployed.
- DNS explained to the user:
  - A `@` → `75.2.60.5`
  - CNAME `www` → `orbis-corporate-review.netlify.app`

**Not done / open:**
- Test form submission: blocked by this environment's network (403 to api.web3forms.com). It was **never** confirmed that a submission arrives.

---

## 2. Hermont website (hermont.in)

**Done (deployed, before/after verified):**
- Grievance Officer email placeholders changed to `connect@hermont.in`.
- On `/services/offshore-business-support`, the Orbis logo links to orbiscorpsol.com.

---

## 3. Podcast episode analysis

**Source:** Google Drive video (`pod3`, 480p).

**Done:**
- Audio transcribed with faster-whisper large-v3-turbo (Hindi and English passes, word timestamps).
- Frame and shot analysis: OpenCV face detection and shot clustering.
- Clip research report:
  - Clean version: https://claude.ai/artifact/UJXpckEeEDsiUVSxpNc4so
  - Handwritten "iPad notebook" version: https://claude.ai/artifact/8CVR6nH5mfpvM4ZJ91rvQo ("How I did this" section removed on request)
  - PDF of the notebook version: `Pod3_Clip_Research_Notebook.pdf` (scratchpad, temporary)

---

## 4. Short-form videos (Reels/Shorts) from the podcast

**Done:** 5 videos rendered and sent to the user in chat.

**Checked on all five:**
- 1080×1920, 30 fps
- Loudness −14.0 LUFS, peaks −1.4 to −1.5 dBFS

| File | Length |
|---|---|
| `01_exit_strategy.mp4` | 40.97 s |
| `02_rich_dont_invest_own_money.mp4` | 43.37 s |
| `03_three_cars_to_no_house.mp4` | 32.20 s |
| `04_sold_out_in_3_months.mp4` | 24.33 s |
| `05_i_sleep_like_a_baby.mp4` | 40.10 s |

**How quality was checked:**
- Contact sheets: one frame every ~1.4 s.
- Caption timings checked against the transcript.
- Videos were **not** watched in real time.

**Fixes after first QC:**
- Two captions had been dropped by an engine bug and are now restored:
  - Clip 03: "because that's what life taught me"
  - Clip 05: "probably I'm not at a very luxury situation"
- Three popups that covered faces were moved lower: 8–9% (02), ₹5,200 and ₹8,500 (04).
- The sleep B-roll in clip 05 was shortened.

**Assets:** all B-roll, music and SFX from Mixkit (free licence). The user should check the Mixkit music terms before posting on a monetised channel.

**Known limit:** the source is 480p, so the speaker is upscaled inside a framed window.

**Not done / open:** only the top 5 clips were edited. The other 11 moments from the research were not.

---

## 5. VANTAJE building: 3D model from floor plans

**Inputs from the user:**
- `L.G_TO_4TH_FLOOR_PLAN.pdf`: 6 pages, in this order:
  1. Ground
  2. Lower Ground
  3. First
  4. Second
  5. Third
  6. Fourth
- A plan image titled "NINETH FLOOR". The user said this is the **typical plan for floors 6–12**, not only the 9th.
- An exterior render video (5 s, aerial dusk view, orange crown with "VANTAJE" on the tower).

**User statements (facts from the user):**
- Floor 5 is a service floor. It is not counted as saleable, but it must still be modelled.
- Floors 6–12 all use the typical plan.

**Done:**
- Interactive 3D model published: https://claude.ai/artifact/69JV1inUgzAnSRY6QSi73e
  - Private; the user must share it from the page's Share menu for others to see it.
  - Not watched for comments: the wake subscription failed to register.
- Levels modelled: LG, G, 1, 2, 3, 4, 5 (service), 6–12 (typical).
- Features:
  - Each floor's real plan image is mapped onto the slab.
  - Walls, columns and cores are traced automatically from the plan drawings and extruded.
  - Atrium and open-to-sky voids are cut through floors 1–4.
  - Views: Exterior, Exploded, Plan view (top-down), Day/Dusk toggle.
- Plan pages were aligned to each other by image registration. Pages 3–6 match within about 1 px; Ground and LG are aligned by scale and offset.

**Data read from the plans (as printed):**
- G-01: 4,759 sq ft. G-56: 3,016 sq ft. Many ground shops are 718 sq ft.
- F-162: 2,085 sq ft (1st floor).
- S-231: 1,096 sq ft (2nd floor).
- T-318A: 2,997 sq ft (3rd floor). Largest open terrace: 993 sq ft.
- 4th floor restaurants:
  - F-419: 6,387 sq ft
  - F-417: 4,905 sq ft
  - F-418: 2,522 sq ft
  - Open sitting terrace: 1,366 sq ft
- Typical office floor, offices x01–x10 (sq ft):

  | Office | 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 | 09 | 10 |
  |---|---|---|---|---|---|---|---|---|---|---|
  | sq ft | 5,249 | 1,528 | 1,268 | 1,871 | 1,485 | 1,450 | 1,722 | 1,625 | 1,237 | 1,649 |

  Total 19,084 sq ft (calculated by summing the labels).

**ASSUMED / estimated (not given in the plans):**
- **Scale:** about 19.3 px/m at 150 dpi, taken from the 7.5 m driveway and 12 m service road on the ground plan. Cross-check: a 584 sq ft shop measures about 635 sq ft.
- **Podium size:** about 133 × 71 m (derived from that scale).
- **Typical floor scale:** about 18.5 px/m, estimated from office areas. Tower about 55 × 48 m.
- **Floor heights** (none were given):

  | Level | Height |
  |---|---|
  | LG | 4.6 m |
  | G | 5.0 m |
  | 1–4 | 4.5 m each |
  | 5 | 4.2 m |
  | 6–12 | 3.9 m each |

  Crown at about 58 m.
- **Tower position on the podium:** placed over the west part to match the render. No plan shows this.
- **Floor 5:** no plan supplied, so it is massing only (service enclosure, podium roof deck, white canopy taken from the render).
- **Exterior:** simplified. The podium's stepped balconies are shown as plain glass floors.
- **Auto-traced walls:** may have small errors or gaps.

**Visual upgrade (version 2, same link):**
- Dusk sky with stars and a glow effect.
- Lit city blocks around the site. These are decorative, not real neighbouring buildings.
- Trees placed on the tree lines drawn on the ground plan.
- Glowing pools at the plan's "water body and cascade" spots.
- Street lamps on the service road, and moving car lights on the main road.
- LED lines under each slab.
- "VANTAJE" sign on the orange crown and a rooftop light beam.
- Roof-deck planters.
- Floating zone labels, an orange outline on the selected floor, an auto-rotating intro and a fly-in.
- Day mode turns most of these off.

**Matched to the render video (version 3, same link):**
- **Tower moved.** It now sits at the back (north), centred on the podium, with the white canopy in front of it at floor 5.
  - Why: in the video the parking lot of white cars is on the right. That parking strip is on the east side of the ground plan, so the video camera must be looking from the south.
  - **ASSUMED:** this position comes from the render, not from any plan.
- **Facade:**
  - Glass set back behind deep white slab edges, like balconies.
  - Glass railings on floors 1–4 and 6–12.
  - Bronze vertical panels on the podium.
  - Planters on the tower balconies.
- **Crown:**
  - Asymmetric orange parapet: lower on the west, taller on the east, with "VANTAJE" on the south face.
  - Glass penthouse with a white roof plate. The light beam was removed.
- **Floor 5** is now shown as recessed dim glazing, as in the render.
  - It is still not saleable per the user; no plan was supplied.
- **Sky and city:** blue dusk sky, paler and lower city blocks, more trees.
- **Site:**
  - Pools with fountain jets and LED rims, plus stepped lawn terraces at the east entry plaza.
  - A row of parked white cars on the plan's parking strip.
- **Camera** now opens from the south-east, high up, like the video.
- **Not matched:**
  - The render's large front plaza with pools on the south side is not in the ground plan, so the pools stay at the plan's east "water body" spots.
  - The podium keeps the plan's footprint (about 133 × 71 m).

**Premium visualisation rebuild (version 4, same link):**
Same floor data and modes; rendering, facade, surroundings, camera and UI rebuilt.

- **Rendering:**
  - Shadows from the sun.
  - Reflections taken from the sky, so glass and pools mirror it.
  - Light glow effect and a slight edge darkening.
- **Lighting presets:** Day, Blue hour and Night, blending smoothly into each other over about 1.6 s.
- **Facade, layered:**
  - Glass at the outside.
  - Lit interior picture behind it, generated by code, not from a photo.
  - Champagne-aluminium mullions and fins; bronze fins on the podium.
  - Dark band at the top of each storey, white slab edges.
  - Glass balustrades with a metal handrail.
  - Planters on the tower balconies.
- **Interior walls:** only shown inside the glass line, so balconies stay clear.
- **Surroundings:**
  - A street grid: avenues to the north, south and west, plus the main road on the east, with pavements and kerbs.
  - Neighbouring buildings made from one design system: shop base, a body with window grid and lit windows, rooftop edge and plant room. Lower near the site, with a park in the south-east foreground.
  - Avenue trees and street lights with pools of light on the ground.
  - About 70 people, about 56 cars (parked and moving), and fountains.
  - **These surroundings are illustrative, not the real neighbourhood.**
- **Camera:**
  - Presets: Hero, Aerial, Street (eye level) and Facade.
  - Eased camera moves.
  - Portrait screens pull the camera back so the whole building fits.
- **Floors and modes:**
  - Click a floor in 3D to select it.
  - Exploded mode animates floors apart, with dashed guide lines.
  - Plan mode looks straight down; floor plans stay readable in any lighting.
- **UI:** dark interface with an Instrument Serif and Inter type pairing, a level index with floor heights, a floor info panel, and a bottom-sheet layout on phones.
- **Tested** at 1440 × 900 and 390 × 844 in a headless browser with a software GPU. Not tested on a real phone GPU.

**Version 5 (same link):**
- **Neighbouring buildings** rebuilt as one design system:
  - Shop base with a white fascia.
  - Main body in one of three facade types (office glass, residential windows with real balconies, or stone pilasters), with a finer grid of 3 m bays and 3.3 m storeys.
  - Upper floors sometimes set back, plus rooftop edges and plant rooms.
  - Lit windows switch on in runs, with gradients, instead of single bright squares.
  - Paved plots around each building.
  - A low, fogged skyline further out for depth.
- **East entry arrival**, all **ILLUSTRATIVE**, not from any drawing:
  - Drop-off lane.
  - Champagne entrance canopy with a lit underside and an orange edge.
  - VANTAJE signage totem.
  - A line of 24 lit bollards.
- **Other changes:**
  - Paved roof deck.
  - Smooth tree canopies in a deeper green.
  - Brighter, cleaner Day preset.
- **Guided "Tour" button:** cycles Hero → Facade → Street → Aerial with a slow orbit. Dragging, changing mode or picking a floor stops it.
- **Tested** in the same headless software-GPU browser at 1440 × 900 and 390 × 844.

**Offered but not done:**
- Flythrough video.
- `.glb` export (Blender, SketchUp, AR).

**Would improve accuracy if the user sends:**
- A section or elevation drawing (real floor heights).
- A site or master plan showing where the tower sits.
- A 5th floor plan.

**Working files (scratchpad, temporary):**
- `.../scratchpad/bldg/`:
  - `extract.py`: plan registration and wall extraction
  - `reg.json`: alignment results
  - `out/index.html` and `out/plan.json`: the viewer and its data
  - `out/tex/*.jpg`: floor textures

---

## Standing rules from the user and the environment
- Execute, don't just plan. Never claim something was done when it wasn't.
- Respect licensing; no watermarked footage.
- Production deploys need the user's explicit go-ahead.
- Don't work around permission or classifier blocks.
- Keep the user's personal details out of external requests.
- No pull requests unless the user asks.

# Decision Log — Ronen Gelmanovich, Unit 2+3

Copy this template into your unit's `student-work/decision-log.md`. Add one
entry per direct → interpret → extend cycle during the supervised-practice
hour. Push to your fork before asking for async help — your reasoning matters
as much as your code.

---

## Cycle 1

- **What I asked**: Visualization of the data over multiple types of map displays.
- **What the agent did**: Created heatmap over the tel aviv area using the dots.
- **What I understood from the result**: Menachem begin road is a very used road, its also very long therefore its the best candidate for the corridor. Also when zooming in I noticed random points scattered in impossible places.
- **My next question / follow-up**: Choose menachem begin road as my corridor.

## Cycle 2

- **What I asked**: visualization of the busies bus lines on menachem begin road
- **What the agent did**: showed me the 4 busiest lines on the road.
- **What I understood from the result**: I saw that none of them had used directly the road, they just crossed it. I saw line 2276 used a pretty large portion of igal alon street.
- **My next question / follow-up**: focus on line 2276 on igal alon street with junctions in itzhak sade and emek bracha.

## Cycle 3

- **What I asked**: Segment igal alon street based on junctions.
- **What the agent did**: Implemented the segementation.
- **What I understood from the result**: Nothing much. 
- **My next question / follow-up**: I predict that the block feeding the hashalom interchange will be the slowest becasue that is a constantly congested main interchange..

## Cycle 4

- **What I asked**: Map-match all bus dots onto the corridor and compute a speed for each block from consecutive same-vehicle ping pairs (±25 m ribbon, Δt 30–120 s, ceiling 80 km/h, dwell kept, pool all lines).
- **What the agent did**: Snapped all dots to the centerline, computed per-pair speeds, and reported pings / samples / median speed per block. (Also fixed a bug where "off-corridor" was measured from the straight chord instead of the curved centerline, which had wrongly thrown out most dots where the road bends.)
- **What I understood from the result**: seg 0 (Yitzhak Sade→Aminadav) is the slowest, ~5 km/h — but it's a very short block terminating in the Aminadav traffic light, so buses crawl the whole way into the queue. The limit there is the junction, not the open road. It also had the fewest samples.
- **My next question / follow-up**: Before forecasting, check how much data each block actually has.

## Cycle 5

- **What I asked**: How dense is each block's time series at 15-min bins (≥3 passes)?
- **What the agent did**: Measured usable bins at 15/30/60-min cadences per block.
- **What I understood from the result**: Bus GPS is too sparse for 15-min bins. seg 0 has **0** usable 15-min bins — it can't be forecast at all; the limit there is the *data*, not the road. Only seg 1 has solid coverage (63% hourly); seg 7 is thin (23%).
- **My next question / follow-up**: Forecast at **hourly** cadence; go deep on seg 1 (dense) and seg 7 (HaShalom); write up seg 0 as data-limited.

## Cycle 6

- **What I asked**: Run the breakeven workflow — ADF, SARIMA(1,1,1)(1,1,1)₂₄, rolling-origin walk-forward vs the historical-average and seasonal-naive floors — on seg 1 and seg 7 at hourly cadence.
- **What the agent did**: Built the hourly series, confirmed stationarity, ran the walk-forward, and found each block's breakeven horizon vs the historical-average floor.
- **What I understood from the result**: seg 1 breakeven = **2 h**, seg 7 breakeven = **4 h**. This overturned my Cycle-3 prediction: **HaShalom (seg 7) is the *more* predictable block, not the least.** Most likely because it's *consistently* congested (steady ~8 km/h, low variance → easy to hit), while seg 1 swings from ~12 to ~25 km/h. Caveat I'm keeping honest about: seg 7 is only 23% real data (heavily interpolated), so part of its low error may be the model predicting our own interpolation rather than real traffic.
- **My next question / follow-up**: Either stress-test seg 7's breakeven with less interpolation, or run the upstream→downstream congestion-lead extension (the Unit 5 seed).

---

## End-of-session rubric check

- [x] DIRECT — phrased requests using unit vocabulary, specified inputs precisely
- [x] INTERPRET — explained results in own words, noticed surprises
- [x] EXTEND — at least one follow-up grounded in a result

## One thing that surprised me today

I predicted the HaShalom interchange block would be the least predictable, but it was the *most* predictable of the two blocks I forecast (breakeven 4 h vs 2 h). A consistently jammed road turns out easier to forecast than a free-flowing one that swings widely — predictability is about *consistency*, not slowness.

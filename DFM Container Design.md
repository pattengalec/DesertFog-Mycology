# Desert Fog Mycology — Container Farm Design
*Consolidated design summary — accessible & standard variants*

---

## 1. Concept & Scope

A single 40ft high-cube shipping container housing the full physical production cycle:
**Sterilization → Inoculation → Growing (spawn run) → Fruiting → Harvesting → Packaging**

Lab/culture work is included inside the container by default, pushed external only if space demands it.

Two build variants share one core system:
- **Accessible version** — pods/tiers on **one wall only**, opposite wall stays clear for wheelchair turning radius and floor equipment.
- **Standard version** — pods/tiers on **both walls**, doubling capacity; either wall's drop-leaf can receive a tray from the opposite wall's tier.

---

## 2. Overall Layout (front to back)

**Entry door → PPE/Hygiene Zone (open, not airlocked) → Floor Zone (autoclave, aisle) → Zone 1 (Culture / Batch A) → Zone 2 (Cold Storage / Batch B) → Waste Chute (far end)**

This mirrors the clean-to-dirty contamination gradient: cleanest work (lab, inoculation) stays furthest from the entry/dirty-exit path; waste exits at the opposite end from where clean material enters.

### Real Dimensions (39'6" / 474" usable interior length)

| Section | Length | Contents |
|---|---|---|
| PPE/Hygiene | ~4ft | Sink, storage, gowning bench |
| Autoclave + clearance | ~5–6ft | Gas autoclave, loading clearance |
| Waste chute + cart dock | ~3ft | Chute, cart docking |
| **Floor zone subtotal** | **~13ft** | |
| **Zone 1** | **~13ft** | Culture (top) / Batch A (bottom) |
| **Zone 2** | **~13ft** | Cold Storage (top) / Batch B (bottom) |
| **Total** | **~39ft** | |

Container envelope: 474" (L) × 92" (W) × 106" (H, high-cube)

### PPE / Hygiene Zone (at entry)
- Open zone, not a sealed airlock (simplicity over rigor, by design)
- Hand hygiene station (sink)
- PPE donning storage (suits, masks, gloves, shoe/hair covers)
- Doffing/disposal bin
- Gowning bench
- General bright, even LED lighting

### Floor Zone
- Gas (propane) autoclave — handles both grain spawn sterilization and bulk substrate sterilization (one method, not split pasteurization/sterilization systems)
- Aisle clearance for movement/turning
- Bright task-oriented LED lighting (controls/gauges visibility, safety around heat-producing equipment)

---

## 3. Vertical Tier System ("airline overhead bin" model)

Two tiers run the length of the cabin along the pod wall(s), each 30" deep:

- **Top tier**: Culture (active lab) + Cold Storage (spawn/culture preservation) — split into two roller-tray lanes, adjacent, so a tray can be pushed laterally from culture directly into cold storage without lifting.
- **Second tier**: Batch A + Batch B — independent inoculation → spawn run → fruiting cycles, each on its own clock, so large orders can be filled without waiting on a single batch's timeline.

**Zone stacking** (simplified to 2 length-zones for build simplicity):
- **Zone 1**: Culture (top) stacked over Batch A (bottom)
- **Zone 2**: Cold Storage (top) stacked over Batch B (bottom)

### Bay Dimensions
- **Depth**: 30" (fixed, drives the laminar airflow path length)
- **Width**: ~80–84" usable (interior width ~92" minus ~8–12" for framing/actuator housing)
- **Tray size**: 18" × 26" (standard half-sheet/bus tray footprint — purchasable, not custom)
- **Trays per bay**: 4 across, with ~4" front-to-back clearance behind the tray within the 30" depth
- Cold storage may stack trays in depth as well, since it doesn't require open laminar-flow clearance

### Behavior
- **Stowed (up)**: sealed, climate-controlled, running its independent environmental program (growing, culture work protected, cold storage held).
- **Lowered (down)**: accessible for work.
- Multi-stop programmable height (wheelchair height / standing height / in-between).

### Lift Mechanism
- Dual synchronized screw-drive linear actuators per bay (acme-thread — self-locking, inherent fail-safe: power loss mid-motion means the tier stays exactly where it is, no free-fall).
- **Designed to accept either manual (hand crank) or powered (motor) drive** on the same shaft/mounting interface — one hardware platform, swappable drive module.
- Shared braking/locking system works regardless of drive type.
- Door motion is tied into the same lift controller — the door only releases once the tier reaches correct working height, so ramp angle is always correct by design.

### Pod Door / Seal
- **Refrigerator-style seal**: magnetic gasket, compression latch — airtight when closed (required for pressure-hood function), simple and proven.
- **Hinges at the bottom**, swings **downward**, doubling as a **ramp/bridge** from the tier shelf down to the drop-leaf below — trays slide down one continuous supported surface, no unsupported gap.
- Door position is sensed for the UV-C interlock (cannot run UV-C unless door is confirmed sealed).

---

## 4. Environmental Control per Bay

### Airflow (laminar flow tunnel design)
- **HVAC/filtered air supply** enters at the **far (rear) wall** of each 30"-deep bay.
- **Reversible fans + dampers** at the **door (front) end** — this is the switchable control point.
  - **Positive pressure mode** (culture bay; inoculation phase of grow bays): air flows out toward the operator at the open door, preventing room contaminants from washing in — same principle as a laminar flow hood.
  - **Negative pressure mode** (fruiting phase of grow bays): reversed — air pulled in at the door, exhausted out the rear filter, protecting the operator/room from spore load.
- **Duct connection**: fixed duct stub on the container's rear wall; pod docks into it only at the **stowed/top position** (sealed connection only when climate control is actually needed — disconnected during lift/lower/open).

### UV-C Sterilization (between-cycle)
- UV-C germicidal fixtures mounted inside each active bay (culture, Batch A, Batch B — cold storage doesn't need this, see below).
- Runs automatically as part of the stow sequence: door closes → UV-C cycle runs → HVAC/pressure re-establishes target climate → tier rises to stow height.
- **Hard door interlock** — UV-C physically cannot run with the door open or a person present.
- Negative pressure during the UV-C cycle helps evacuate residual spore load, not just kill it in place.
- Supplemented by periodic manual wipe-down (UV-C doesn't reach shadows/crevices/organic residue).

### Cold Storage (mechanically lighter — no pressure/laminar/UV-C systems needed)
- Steady refrigeration temp (~34–40°F), sealed, dark.
- Simple insulation + compressor, not a contamination-controlled chamber.
- Nearly permanently stowed; lowered only briefly to pull/add stock.
- Light only on when door/tier is accessed — off otherwise.

### Humidity (fruiting)
- Dedicated clean-water humidifier per grow bay (ultrasonic or evaporative), fed from the cistern — **not** autoclave steam (would breach contamination control and is a burn hazard).

### Interior Lighting (by zone)
- **PPE/Floor zone**: bright, general/task LED.
- **Drop-leaf work surfaces**: dedicated fixtures over each leaf segment (not just ambient) to avoid the operator's own shadow falling across the work.
- **Culture bay**: bright, color-accurate LED for visual contamination inspection.
- **Cold storage**: off by default, on only when accessed.
- **Batch A/B (spawn run → fruiting)**: staged and automated as part of the same bay controller already sequencing pressure mode/HVAC/UV-C — dark during spawn run, light during fruiting, matching a natural photoperiod cue.
- **Standing principle, applies system-wide**: every automated system (pressure mode, HVAC, UV-C, lighting, lift) retains a **manual override** — temporary/reversible, resumes the automatic schedule once released. Not unique to lighting.

---

## 5. Tray & Material Transfer

- **Roller trays** — the core transfer unit throughout. Nothing is carried; everything slides.
- **Culture ↔ Cold Storage**: lateral tray push along a shared rail, same tier.
- **Tier → Drop-leaf**: tray slides down the open door/ramp directly onto the leaf below.
- **Drop-leaf design**: segmented to match the tier's internal partitions above it (independently deployable — only the leaf segment aligned with an active bay needs to unfold, keeping the aisle otherwise clear).
- **Leaf placement**:
  - *Accessible version*: leaves on the wall **opposite** the tiers, so trays have a clear path across the aisle.
  - *Standard version*: leaves stowed under tiers on **both** walls; either wall's tier can feed either wall's leaf.

---

## 6. Waste Flow (solid, dirty-out)

- **One chute**, single wall penetration, at the **far end of the container, opposite the PPE/entry zone** — true end-to-end clean-in/dirty-out flow.
- **Wheeled cart on a floor-level guide track**, running the full length **underneath the drop-leaf run**, front to back.
  - Simple guided track (not the precision tray-rail system) — appropriate for bulk/heavier cargo, low physical effort, no steering required.
  - Waste loads into the cart locally wherever it's generated along the route.
  - Cart terminates at the chute for final disposal into an external cart.
- This keeps spent substrate from ever crossing the clean entry path.

---

## 7. Power System

- **Primary**: Roof-mounted solar array + battery bank.
  - Roof area ~250–280 sq ft usable → roughly 12–15 panels, ~4.5–6kW peak capacity.
  - Covers the modest continuous load (HVAC ×4 bays, actuators, fans/dampers, UV-C, lighting) — estimated 1–2kW without the autoclave.
- **Backup/top-off**: **3–4kW rated propane generator**, sized purely to the electrical top-off load. Recharges battery during low-solar stretches. Propane chosen over gasoline/diesel for storage stability (doesn't degrade sitting unused).
- **Autoclave**: Propane-fired, **same shared tank system** as the generator, separate regulated line — a direct gas burn, not an electrical draw, so it never competes with the generator's output. Pulled off the electrical system entirely — it was the one load that would have broken a pure solar/battery budget (3–6kW thermal while heating).
- **Shared propane tank**: 250-gallon tank, ~2.5–5 month refill cadence under combined autoclave (~30–60 gal/month) + generator (~20–40 gal/month) draw — worst-case simultaneous-use day (~3–10 gallons) well within tank margin.
- **No grid dependency** — fully self-contained system (grid tie-in intentionally dropped in favor of the generator).

---

## 8. Water System (fully closed-loop)

- **Cistern** (delivered supply, **1,000–1,500 gallons**, ~2–4 week delivery cadence) → feeds hand hygiene sink, autoclave (fresh fill), pod humidifiers.
- **Light greywater** (hand-hygiene-sink water only): filtered, recycled into the **autoclave**.
- **Process greywater** (cleaning/sanitizing wastewater): collects until tank is full → released through **rooftop emitters** → washes dust off solar panels.
- **Roof pitch**: roof is pitched **side-to-side (across the width)**, not front-to-back — water sheets across and evaporates in transit rather than pooling, avoiding any standing-water structural load. Pitch direction chosen specifically so runoff crosses **over the cold storage section locally**, independent of where Zone 2 falls along the container's length — decouples roof drainage from floor-plan zone ordering.
- **Gutter**: runs along **one long side edge** of the roof, positioned near Zone 2/cold storage for a short plumbing run.
- **Gutter output**: captured in a **barrel** for external reuse (irrigation elsewhere on site, etc.) — not discharged to ground.
- No dangling waste stream — every drop of water has a defined next use.
- Solar panels sit on their own racking/leveling, independent of roof pitch.

---

## 9. Safety & Contamination Control Summary

- Clean-to-dirty gradient physically encoded in the floor plan (entry/PPE → clean work → dirty exit), not just procedural.
- Refrigerator-style seals maintain pressure-hood integrity.
- UV-C interlocked to door position — cannot operate with door open.
- Self-locking screw-drive actuators provide inherent fail-safe against free-fall on power loss.
- Autoclave fuel (propane) fully isolated from the electrical system — no shared point of failure with HVAC/lighting/actuators.

---

## 10. Open / Deferred Items (not yet designed — flagged, not forgotten)

- Real dimensioning: exact bay widths, Zone 1/Zone 2 length split, autoclave footprint, cistern and propane tank sizing.
- Exterior skin, signage, branding treatment (blue-oyster lab aesthetic).
- Interior lighting design/fixtures beyond "LED throughout."
- Roof catch-basin structural load and waterproofing detail.
- Generator sizing vs. simultaneous autoclave + battery-topping propane draw.
- Component sourcing/costing (deliberately deferred until design was locked).

---

*This document reflects the fully-imagined design as developed in conversation. Next step: build a physical/visual model.*

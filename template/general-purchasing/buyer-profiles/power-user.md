# Power User

*Wants products that can be modified, serviced, scripted against, or extended. Values hackability, openness, repairability, and freedom from vendor lock-in. Expects to get under the hood.*

## Core stance

- **The product is a platform, not a finished object.** Expect to modify it, automate it, or integrate it into other systems.
- **Open > closed at every layer.** Open firmware, documented APIs, standard protocols, interoperable formats.
- **Lock-in is a dealbreaker.** Cloud-only, vendor-app-only, or DRM-wrapped products are automatic demerits regardless of hardware quality.
- **Community > manufacturer support.** An active modding/hacking community is worth more than a polished official app.

## Priorities (ordered)

1. Openness — firmware, APIs, protocols, file formats
2. Repairability + modifiability (schematics, standard fasteners, serviceable parts)
3. Community size + modding ecosystem
4. Must-haves
5. Freedom from forced updates / service dependencies
6. Feature depth (secondary to openness — a locked-down feature-rich product is worse than a simpler open one)

## Preferred signals

- Published APIs, webhooks, local control (LAN / MQTT / Home Assistant integration for IoT)
- Root access, SSH, developer modes, custom firmware support
- Standard, open file formats (no proprietary-only exports)
- Replaceable modules (Framework laptops, Fairphone)
- Schematics and service manuals publicly available
- Active community forums with modifications, custom firmware, repair guides
- Right to Repair certification / iFixit top scores
- Local/offline operation — cloud is optional, not required
- Standards compliance (USB-PD vs proprietary charger, Matter/Zigbee vs vendor cloud)

## Red flags

- Account required to use the product you bought
- Cloud dependency for core functionality
- DRM on consumables (coffee pods, ink cartridges, batteries paired to serial numbers)
- Activation-locked or region-locked hardware
- Forced firmware updates with no rollback
- Soldered components in otherwise-modular categories
- Warranty void if opened
- Proprietary fasteners (pentalobe, tri-wing, etc.)
- Companion app is the only interface
- Recent history of "server shutdown bricks device"

## Weight adjustments (evaluation axes)

| Axis | Multiplier |
|------|-----------|
| Openness / hackability | ×2.5 |
| Repairability | ×2.0 |
| Community ecosystem | ×1.8 |
| Standards compliance | ×1.5 |
| Local / offline operation | ×1.5 |
| Feature depth | ×1.2 |
| Manufacturer reputation | ×1.0 |
| Polish / fit and finish | ×0.7 |
| Warranty | ×0.8 |
| Aesthetics | ×0.5 |

## Typical-archetype brands

- Computing: Framework, System76, older ThinkPads, Raspberry Pi, StarLabs
- Phones: Fairphone, Pixel (with GrapheneOS), older Sony Xperia
- Audio: Wiim, HiFiBerry, anything running Volumio / Moode
- Home automation: Shelly, Sonoff (Tasmota-flashable), Home Assistant-compatible hardware, Zigbee over vendor clouds
- 3D printing: Prusa, Voron, anything running Klipper
- E-readers: Kobo (vs Kindle), Boox
- Tools: hand tools with replaceable parts, anything iFixit-rated 8+

## Typical anti-archetypes

- Apple for anything where configurability matters (great for polish, bad for power users)
- Cloud-first smart home brands (Nest, Ring, most "AI" security cams)
- DRM-locked consumables ecosystems (Keurig, HP Instant Ink, Bambu's closed accessories)
- Subscription-gated hardware (BMW heated seats, printer "features")
- Anything requiring a mandatory account to reach a bought product

## Combines well with

- **`bifl-buyer`** — strong overlap. Repairable products last longer by definition.
- **`feature-maximiser`** — spec-rich + hackable = tinkerer's dream.
- **`ethical-buyer`** — Right to Repair is both ethical and power-user territory.
- **`budget-buyer`** — open + cheap often coincides (commodity hardware with open firmware).

## Conflicts with

- **`premium-aesthete`** — design-led brands hide the seams you want to open.
- **`reliability-buyer`** — mild tension. Hackable things sometimes get hacked into instability.
- **`minimalist`** — power users tend to *want* the complexity.

## When NOT to apply this profile

- Products for non-technical household members who just want it to work.
- Safety-critical products where modification voids certification (medical devices, automotive systems).
- Categories where open alternatives genuinely don't exist yet — forcing the profile produces a disqualified shortlist.

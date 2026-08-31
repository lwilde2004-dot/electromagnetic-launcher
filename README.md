# Single-Stage Coilgun

A capacitor-discharge electromagnetic launcher, designed from scratch and built at home. It accelerates a 4.5 mm steel BB with a single coil, and the design is deliberately held to a low-energy bench demonstrator.

**Status:** design and bill of materials complete, parts being ordered. Nothing energised yet, so every figure below is predicted rather than measured.

---

## Target specification

| | |
|---|---|
| Projectile | 4.5 mm steel BB, 0.35 g |
| Stored energy | 10–40 J |
| Muzzle velocity | 40–80 m/s predicted |
| Muzzle energy | 0.3–1.2 J |
| Efficiency | 1–5% (typical for a single stage) |
| Cost | £70–140 including protection and instrumentation |

## How it works

Charge a capacitor bank to a few hundred volts, then dump it through a coil in a few milliseconds. The coil pulls the ferromagnetic projectile toward its centre. Switch off before the projectile reaches that centre and it flies out; leave the coil energised a moment too long and the same field drags it back. That timing problem is most of the engineering, and it is why single-stage efficiency sits in the low single digits.

## Sizing

Bank energy is `E = ½CV²`. At an assumed 3% transfer efficiency, a 20 J bank delivers roughly 0.6 J to the pellet:

```
v = sqrt(2E/m) = sqrt(2 × 0.6 / 0.00035) ≈ 59 m/s
```

Muzzle energy lands near 0.6 J. Pushing the bank to 40 J gives about 83 m/s and 1.2 J, which crosses a line I would rather stay under (see Legal).

The light pellet is the whole trick. A marble-sized slug weighs 20 to 50 times more, so reaching the same speed needs a bank big enough to be genuinely dangerous.

## Design choices

**200 V bank, not 400 V.** Roughly 1000 µF at 200 V gives 20 J. A 250 µF photoflash bank at 350–400 V gives similar energy in a smaller package, but 400 V is far less forgiving of a mistake. For a first build the bulkier, lower-voltage option is the right trade.

**SCR, not IGBT.** An SCR is a simpler switch and adequate for these currents. The cost is real and worth stating: an SCR cannot be commutated off on demand, so pulse timing has to come from the coil and bank characteristics rather than from the gate. An IGBT with a driver would give proper turn-off control, and that is the obvious upgrade when the timing becomes the limiting factor.

**Coil:** 20–24 AWG enamelled copper, 200–400 turns in 4–6 layers, 20–30 mm long, targeting 100–500 µH at 0.3–0.6 Ω.

## Safety

The capacitor bank is the hazard, not the projectile. A charged bank can deliver a lethal shock in milliseconds, and it stays charged after the supply is disconnected.

- Permanent bleed resistor across the bank
- HV-rated meter, and the bank confirmed at zero before anything is touched
- One hand only when working near a charged bank
- Fired indoors into a solid backstop, as a bench demonstrator

## Legal (UK)

A coilgun is not an air weapon in law, so the air weapon energy limits do not cleanly apply. Muzzle energy above roughly 1 J is where a device starts to look like a firearm rather than a toy. The v1 design is constrained to sit at or below that line, and that constraint is why the pellet is light and the bank is small. Any scale-up to a marble-sized slug would push well past it and is not something I intend to build.

## Next

- [ ] Wire the equivalent circuit at 9 V and check the discharge trace against prediction
- [ ] Order the bank, charger and switching parts
- [ ] Wind and characterise the coil (measure L and R against target)
- [ ] Measure muzzle velocity and compare against the 59 m/s prediction

# Single-Stage Electromagnetic Launcher

A capacitor-discharge coil launcher (a coilgun), designed from scratch to be built at home. It is sized to accelerate a 4.5 mm steel BB with a single coil, and the whole design is held under the legal energy ceiling described below.

**Status:** design and bill of materials complete, parts being ordered. Nothing has been energised yet, so every figure here is predicted rather than measured.

---

## Target specification

| | |
|---|---|
| Projectile | 4.5 mm steel BB, 0.35 g |
| Stored energy | 10–30 J |
| Muzzle velocity | 40–70 m/s predicted |
| Muzzle energy | 0.3–0.9 J, hard ceiling 1 J |
| Efficiency | 1–5%, typical for a single stage |
| Cost | £70–140 including protection and instrumentation |

## How it works

Charge a capacitor bank to a few hundred volts, then dump it through a coil in a few milliseconds. The coil pulls the ferromagnetic projectile toward its centre. Switch off before the projectile reaches that centre and it flies out; leave the coil energised a moment too long and the same field drags it back. Getting that timing right is the hard part, and mistiming it is why single-stage efficiency is only a few percent.

## Sizing

Bank energy is `E = ½CV²`. At an assumed 3% transfer efficiency, a 20 J bank delivers roughly 0.6 J to the pellet:

```
v = sqrt(2E/m) = sqrt(2 × 0.6 / 0.00035) ≈ 59 m/s
```

That puts muzzle energy at about 0.6 J, comfortably under the ceiling.

The pellet mass is what keeps the energy down. A marble-sized slug weighs 20 to 50 times more, so reaching the same speed would need a bank big enough to kill you.

## Design choices

**Why 200 V.** Roughly 1000 µF at 200 V gives 20 J. A 250 µF photoflash bank at 350–400 V gives similar energy in a smaller package, but 400 V is far less forgiving of a mistake. For a first build I would rather have the bulkier, lower-voltage version.

**Switching.** An SCR is the simpler switch and handles these currents fine. The downside is real: an SCR cannot be commutated off on demand, so pulse timing has to come from the coil and bank characteristics rather than from the gate. An IGBT with a driver gives proper turn-off control, and that is the upgrade once timing becomes what limits performance.

**Coil.** 20–24 AWG enamelled copper, 200–400 turns in 4–6 layers, 20–30 mm long, targeting 100–500 µH at 0.3–0.6 Ω.

## Safety

The capacitor bank is the hazard, not the projectile. A charged bank can deliver a lethal shock in milliseconds and stays charged after the supply is disconnected.

- Eye protection worn whenever the bank is charged
- Insulated shorting stick used to discharge the bank before any work on it, with the permanent bleed resistor treated as a backup rather than the primary means
- Bank confirmed at zero on an HV-rated meter before anything is touched
- One hand only when working near a charged bank
- Never worked on alone
- Never pointed at a person or animal, charged or not
- Fired only into a dedicated backstop of steel plate behind timber, indoors, as a bench demonstrator

## Legal position (UK)

Under the Firearms Act 1968 as amended by the Policing and Crime Act 2017, a "lethal barrelled weapon" is a barrelled weapon from which a missile with kinetic energy of **more than one joule at the muzzle** can be discharged. A coilgun has a barrel and gets none of the air-weapon exemptions, so one joule is a hard ceiling rather than a guideline: above it, the device is a Section 1 firearm and needs a certificate.

The design sits under that ceiling by choice, and that constraint is why the pellet is light and the bank is small. Scaling to a marble-sized slug would go straight past it, and I am not building that.

## Next

- [ ] Wire the equivalent circuit at 9 V and check the discharge trace against prediction
- [ ] Order the bank, charger and switching parts
- [ ] Wind and characterise the coil, measuring L and R against target
- [ ] Measure muzzle velocity and compare against the 59 m/s prediction

## Licence

Text and diagrams CC BY 4.0.

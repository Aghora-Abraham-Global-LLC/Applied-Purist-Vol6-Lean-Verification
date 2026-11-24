# Applied Purist Vol. VI — Lean 4 Formal Verification (`PuristSiliconCore`)

Lean 4.36.0 / Lake 5.0 formal verification suite (**55 `KERNEL_ONLY` theorems, `0 sorry`**, zero Mathlib) + freestanding C99 constant-time kernel (`c_silicon/solinas_ct.c`) for **Applied Purist Vol. VI** (`10.5281/zenodo.24392562`) & `https://lean.bhutadamarasena.com/`.

## Reproduce
`lake build && lake exe purist_audit ./proof-manifest.json`

## Coverage & Scope Boundaries
- **Universally Proven (`KERNEL_ONLY`, `0 sorry`):** 2-pass/3-pass Solinas folding (`p64`, `p106`), `addModP64Ct`/`subModP64Ct`, 9-mul `F_{p64^4}` Karatsuba; centered `D106` injectivity, `rotl_64` inverse & `popcnt64` invariance, Morton-30 masking; Relaxed-R1CS zero-slack folding & bijective 46-bit NTT packing; 64B `SolinasIvcState64` ABI & SP 800-88 wipe.
- **Mathlib-Deferred Boundary:** `Anchor.lean` checks congruences & Euler modular powers via `rfl`; formal `Nat.Prime` certificates, polynomial irreducibility (`X^4 - 2`), general `MvPolynomial` Schwartz–Zippel, and IEEE-754 `Float` bit semantics remain outside this Mathlib-free core.
- **OPSEC Boundary:** Proprietary `TMD-Hash v11.0/v12.0` internals & NUMS constants excluded (`TMD12-BB` black-box only).
# Applied-Purist-Vol6-Lean-Verification

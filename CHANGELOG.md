# Changelog

## 1.1.0 — 2026-08-27

### Changed

- Changed the molecular orientation convention so π stacking is aligned with z rather than y.
- Atom pair A→B now defines the positive x direction.
- Atom pair C→D now supplies the positive y direction after orthogonalization against x.
- The right-handed cross product x × y defines the positive z direction and molecular-plane normal.
- The default `tz` separation and `rz` rotation therefore operate directly along and around the π-stacking axis after orientation.

### Added

- Optional RGB coordinate axes: x red, y green, and z blue.
- Optional translucent full-size van der Waals spheres for inspecting intermolecular contact.

### Compatibility note

Earlier versions mapped C→D to z, leaving y as the normal when both reference vectors were in the molecular plane. Existing XYZ inputs still work, but orientation choices and grids from earlier versions should be checked and remapped before reuse.

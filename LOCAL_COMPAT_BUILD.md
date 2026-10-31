# Local AE2 UEL compatibility build

Source: AE2-UEL/Applied-Energistics-2 `master` at `724ffaebe3a8ba7d2320431acf03a8c2f6345d9e`.

Included upstream changes:
- [#591](https://github.com/AE2-UEL/Applied-Energistics-2/pull/591), HEI ghost/bookmark handling (already present in the master base).
- [#586](https://github.com/AE2-UEL/Applied-Energistics-2/pull/586), collision-safe AE item stack registry (ported from triage).
- [#554](https://github.com/AE2-UEL/Applied-Energistics-2/pull/554), fluid P2P attunement using the correct part (ported from triage).
- [#553](https://github.com/AE2-UEL/Applied-Energistics-2/pull/553), 9 interface pattern slots per pattern expansion group (ported from triage).

Build: GitHub Actions `.github/workflows/build.yml` uses Java 17, Gradle wrapper and **does not** run `updateBuildScript`. Upstream's previous build failures arose because that task overwrote a usable RetroFuturaGradle version with 1.4.0 during CI.

## Validation
- Build pass alone is not gameplay validation.
- Test on a backed-up copy of the world with AE2 UEL, AE2 FCR, NAE2 (Sept 27 baseline), AE2 Stuff, GTCEu and HEI.
- Confirm correct fluid P2P bucket attunement, HEI terminal ghost/bookmark transfers, Memory Card pattern copying, circuit recipes and Dual Interface operation.
- Test item variants with colliding hashes in isolated fixtures before trusting valuable storage.
- Use the **runtime** AE2-UEL jar in `build/libs`, not `-dev`, `-api` or `-sources`; keep only one AE2 JAR installed.

## GitHub Actions trigger
This development branch builds on pushes and manual workflow dispatch. If a newly forked repository had Actions disabled when the first commit was pushed, this documentation update triggers a fresh build after enabling Actions. Select the runtime mod JAR from the completed workflow artifact.

# Release notes template

Shared template for PowSyBl repositories release notes.
Copy the body below into the GitHub release, remove the sections that do not apply, and keep the section order.

---

<!-- Optional: only when a migration guide exists for this version -->
*To fix any issues due to migration, please go to the [migration guide](https://github.com/powsybl/REPO/wiki/Migration-guide-vX.Y.Z). Labels are clickable and lead to the section of the migration guide corresponding to the associated described change.*
- ![Deprecated](https://img.shields.io/badge/-Deprecated-blue.svg) indicates that some methods were deprecated;
- ![Breaking Change](https://img.shields.io/badge/-Breaking%20Change-red.svg) indicates a breaking change which could impact all users;
<!-- Only for repositories exposing a custom IIDM implementation API (e.g. powsybl-core) -->
- ![Custom IIDM Impl](https://img.shields.io/badge/Custom%20IIDM%20Impl-8A2BE2.svg) indicates a breaking change impacting only custom IIDM implementations (most of the time, new IIDM methods/classes to implement). Note that this label is not added when another breaking change impacting all users is also present.

<br/>

<!-- Optional: 1 to 5 highlights for the release -->
# ⭐ Key features
- TBD

<!-- Optional: important information for users, e.g. a release skipped on Maven Central -->
## Note
- TBD

# 📜 Release notes

<!-- Security fixes first, when any -->
## 🛡️ Vulnerability fixes
- TBD

## 🪲 Fixes
- TBD

## 💎 Quality
- TBD

## 📚 Documentation
- TBD

## 🕸️ Dependencies
- TBD

| Library / component | Previous version | New version | PR |
| --- | --- | --- | --- |
| TBD | TBD | TBD | #TBD |

---

**Conventions**
- Use `vX.Y.Z` for the release tag. Release candidates (`vX.Y.Z-RCn`) use the same template, with `- **TBD**` under key features until finalized.
- Each item ends with its PR number in parentheses, e.g. `(#4177)`; use several numbers when a change spans PRs, e.g. `(#4175, #4176)`.
- Prefix bug fixes with `fix:` when it helps scanning; otherwise keep the imperative form (`Fix ...`, `Add ...`, `Update ...`).
- Section headings are chosen per release; keep the order: Key features, Note, Vulnerability fixes, module sections, Fixes, Quality, Documentation, Dependencies.
- Omit empty sections.

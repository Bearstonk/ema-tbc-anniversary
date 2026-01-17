# Changelog

All notable changes to the EMA TBC Anniversary Edition fork are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added
- API compatibility layer for cross-version support
  - `GetAddOnMetadataCompat()` - Safe addon metadata retrieval across WoW versions
  - `IsAddOnLoadedCompat()` - Safe addon detection across WoW versions
  - Exported in `EMAPrivate.Core` for module access

- Documentation
  - Comprehensive README.md with installation and configuration guide
  - ISSUES.md with testing checklist and feature requests
  - CHANGELOG.md (this file)

### Changed
- Core.lua refactored to use compatibility wrapper functions
  - Updated version detection to use `GetAddOnMetadataCompat()`
  - Updated Jamba detection to use `IsAddOnLoadedCompat()`
  - Exported compatibility functions for use by other modules

- DisplayTeam.lua updated for TBC compatibility
  - TrufiGCD detection now uses `IsAddOnLoadedCompat()`
  - Multiple instances (lines 29, 3251, 3268) updated

- Quest-Classic.lua updated for TBC compatibility
  - ElvUI detection now uses `IsAddOnLoadedCompat()` (line 1959)

### Fixed
- Cross-version API compatibility issues
  - Resolved nil value errors when calling C_AddOns on older WoW versions
  - Safely handles both new (C_AddOns namespace) and old (global functions) APIs

### Tested
- ✅ Addon loads without Lua errors
- ✅ API compatibility functions available
- ✅ Module compatibility layer working
- ⏳ Full gameplay testing pending

---

## [Release-v4.3(0243)] - Base Version

### Info
- Based on upstream EMA Release-v4.3(0243)
- Commit: ef79c96 "Release-v4.3(0243) error on live TOC"
- Source: https://github.com/ebonyfaye/ema/releases/tag/Release-v4.3(0243)

### Base Features (from v4.3)
- Team management and character tracking
- Party/raid coordination
- Keybinding system (10 focus keys, multiple command keys)
- Item usage synchronization
- Quest tracking and synchronization
- Macro support for multiboxing
- Cross-realm functionality
- Settings persistence
- Multiple module system

---

## Planned Releases

### v0.4(0244) - TBC Stability Release
**Goal:** Ensure stability in TBC Classic Anniversary Edition

- [ ] Complete testing of all modules
- [ ] Resolve any TBC-specific bugs
- [ ] Integrate TBC-specific optimizations
- [ ] Update keybindings if needed
- [ ] Release stable version

### v0.5(0245) - Feature Release
**Goal:** Add TBC-specific features and enhancements

- [ ] TBC-specific quest features
- [ ] TBC reputation tracking
- [ ] Enhanced macro templates
- [ ] Settings profiles
- [ ] Performance optimizations

---

## Version History

### Current Branch: tbc-anniversary

```
973e84a (HEAD -> tbc-anniversary) docs: Add comprehensive README for TBC Anniversary fork
b2d3d42 Apply PRs: Add API compatibility layer and update modules (PRs #142-#144)
ad5a226 refactor: update Core.lua to use API compatibility functions
8260f47 feat: add API compatibility layer for cross-version support
ef79c96 (tag: Release-v4.3(0243)) Release-v4.3(0243) error on live TOC
```

---

## Related Versions

- **Upstream Latest:** EMA v4.7(0270)
  - Source: https://github.com/ebonyfaye/ema
  - Note: This fork maintains v4.3(0243) for TBC Anniversary focus

- **David-c0degeek Fork:** Also TBC-focused (v4.3(0231))
  - Source: https://github.com/David-c0degeek/ema
  - Used as reference for TBC compatibility

---

## How to Report Changes

When you make changes, update this file:

```markdown
### [Version Number] - Date (e.g., YYYY-MM-DD)

#### Added
- New features

#### Changed
- Modified behavior

#### Fixed
- Bug fixes

#### Removed
- Removed features

#### Tested
- What was tested
```

---

## Contributing

See [ISSUES.md](ISSUES.md) for testing checklist and known issues.

To contribute a fix or feature:
1. Create a branch from `tbc-anniversary`
2. Make your changes
3. Add entry to this CHANGELOG
4. Submit a pull request
5. Update version tag when merged

---

## Version Numbering

Format: `v[BaseVersion]([BuildNumber))-TBC`

Example: `v4.3(0244)-TBC`

- **BaseVersion:** EMA version (e.g., 4.3)
- **BuildNumber:** Incremental build counter (e.g., 0244, 0245)
- **Suffix:** "-TBC" to indicate TBC Anniversary fork

---

**Last Updated:** January 17, 2026  
**Maintained by:** Bearstonk  
**License:** All Rights Reserved 2018-2026 Jennifer Calladine (Ebony) and Contributors

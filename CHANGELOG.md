# Changelog

All notable changes to the EMA TBC Anniversary Edition fork are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [v4.3(0243)-TBC-Anniversary] - 2026-01-17

### Added
- **API Compatibility Layer** for cross-version support
  - `GetAddOnMetadataCompat()` - Safe addon metadata retrieval across WoW versions
  - `IsAddOnLoadedCompat()` - Safe addon detection across WoW versions
  - Exported in `EMAPrivate.Core` for module access
  - Handles both C_AddOns namespace (Retail) and global functions (Classic/TBC)

- **TBC TOC Files**
  - Created `EMA_TBC.toc` with interface version 20504
  - Created `ema-tbc-anniversary.toc` for folder name matching
  - Updated `EMA.toc` to interface 20504 for TBC Anniversary

- **Fork Attribution**
  - GUI displays fork maintainer: Tom Williams (Bearstonk)
  - Added [BETA/IN TESTING] warning in orange
  - Updated copyright to include fork year and maintainer
  - Preserved original author attribution (Jennifer Calladine)

- **Documentation**
  - Comprehensive DEVLOG.md documenting development decisions
  - README.md with installation and troubleshooting guide
  - ISSUES.md with testing checklist and bug tracking
  - CHANGELOG.md (this file)

### Changed
- **Core.lua** - Refactored for TBC compatibility
  - Version detection uses `GetAddOnMetadataCompat()`
  - Addon detection uses `IsAddOnLoadedCompat()`
  - Exported compatibility functions for module use

- **DisplayTeam.lua** - TBC compatibility updates
  - TrufiGCD detection moved from load-time to OnInitialize()
  - Uses `EMAPrivate.Core.IsAddOnLoadedCompat()` (lines 29, 3251, 3268)

- **Quest-Classic.lua** - TBC compatibility
  - ElvUI detection uses `IsAddOnLoadedCompat()` (line 1959)

- **6 Modules** - Added safety checks for Core function availability
  - Bank.lua, Trade.lua, Toon.lua, Sell.lua, Purchase.lua, Interaction.lua
  - Prevents nil errors when modules load before Core completes

### Fixed
- **Critical: Database Initialization Timing** (Issue #1)
  - Fixed `attempt to index field 'db' (a nil value)` in QuestWatcher-Classic
  - Added nil checks to 8 functions before accessing `EMA.db`
  - Functions: EMAQuestWatcherUpdate, CanDisplayQuestWatcher, SetQuestWatcherVisibility, UpdateUnlockWatcherFrame, UpdateHideBlizzardWatchFrame, UpdateQuestWatcherDimensions, SettingsUpdateBorderStyle, SettingsUpdateFontStyle

- **Critical: Module Load-Order Errors** (Issue #2)
  - Fixed nil errors from calling `EMAPrivate.Core.isEmaClassicBccBuild()` too early
  - Added existence checks before calling Core functions in OnEnable()
  - Affected modules: DisplayTeam, Bank, Trade, Toon, Sell, Purchase

- **Critical: TOC Configuration** (Issue #3)
  - Fixed addon not loading due to wrong interface version
  - Changed from interface 100100 (Retail) to 20504 (TBC Anniversary)
  - Ensures addon loads correctly in WoW Classic: Burning Crusade Anniversary

- **Cross-Version API Compatibility**
  - Resolved nil value errors when calling C_AddOns on TBC
  - Safely handles both new (C_AddOns namespace) and old (global functions) APIs

### Known Issues
- LibBagUtils import errors in multiple modules (TBC library compatibility)
- InterfaceOptions_AddCategory is nil in EMAHelperSettings.lua (TBC UI framework difference)
- Various runtime errors from library compatibility (non-critical, under investigation)

### Tested
- ✅ Addon loads successfully in TBC Anniversary
- ✅ Configuration UI opens with `/ema config`
- ✅ Team window displays team members
- ✅ No critical Lua errors on load
- ✅ API compatibility functions working
- ⏳ Full module testing in progress
- ⏳ Extended gameplay testing pending

### Migration Notes
For users upgrading from upstream EMA or previous versions:
1. Disable old EMA version in addon list
2. Install this fork as separate addon
3. Configuration should be preserved (uses same SavedVariables)
4. Report any issues to GitHub repository

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

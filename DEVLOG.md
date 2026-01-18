# Development Log - EMA TBC Anniversary Fork

## Project Overview
Independent fork of EMA (Ebony's MultiBoxing Assistant) specifically for WoW Classic: Burning Crusade Anniversary Edition. This fork applies critical API compatibility fixes and serves as a testing ground for TBC-specific features.

**Fork Maintainer:** Tom Williams (Bearstonk)  
**Original Author:** Jennifer Calladine (Ebony)  
**Base Version:** Release-v4.3(0243)  
**Fork Version:** Release-v4.3(0243)-TBC-Anniversary  
**Status:** Beta / In Testing

---

## January 17, 2026 - Initial Fork Setup and API Compatibility

### Objective
Create a stable, working version of EMA for TBC Anniversary by backporting critical API compatibility fixes from the 0270 development branch.

### Base Version Selection
**Decision:** Use v4.3(0243) instead of v4.3(0230)
- **Rationale:** 0243 is more stable with additional bug fixes
- **Source:** Tagged release `Release-v4.3(0243)` (commit ef79c96)
- **Alternative Considered:** v4.3(0230) was the originally requested version but lacked important stability improvements

### Pull Requests Integrated

#### PR #142 - Core API Compatibility Layer
- **Commit:** c5d987b from ebonyfaye/ema branch `Dev-v4.3(0270)`
- **Changes Applied:**
  - Added `GetAddOnMetadataCompat()` wrapper function
  - Added `IsAddOnLoadedCompat()` wrapper function
  - Handles C_AddOns namespace (Retail) vs global functions (Classic/TBC)
  - Exported functions via `EMAPrivate.Core`
- **Files Modified:**
  - `Core/Core.lua` - Added compatibility layer (lines 14-33, 42-45)
- **Why Needed:** WoW API changed in Retail to use C_AddOns namespace; TBC uses global functions

#### PR #143 - DisplayTeam.lua TrufiGCD Compatibility
- **Commit:** 90700b9 from ebonyfaye/ema branch `Dev-v4.3(0270)`
- **Changes Applied:**
  - Updated TrufiGCD addon detection at lines 29, 3251, 3268
  - Changed from `IsAddOnLoaded()` to `EMAPrivate.Core.IsAddOnLoadedCompat()`
- **Files Modified:**
  - `Modules/DisplayTeam.lua`
- **Why Needed:** Ensures TrufiGCD integration works across all WoW versions

#### PR #144 - Quest-Classic.lua ElvUI Compatibility
- **Commit:** e48ffc0 from ebonyfaye/ema branch `Dev-v4.3(0270)`
- **Changes Applied:**
  - Updated ElvUI detection at line 1959
  - Changed from `IsAddOnLoaded()` to `EMAPrivate.Core.IsAddOnLoadedCompat()`
- **Files Modified:**
  - `Modules/Quest-Classic.lua`
- **Why Needed:** Ensures ElvUI integration works across all WoW versions

### Critical Bug Fixes

#### Issue #1 - QuestWatcher Database Initialization Timing
- **Problem:** `attempt to index field 'db' (a nil value)` at QuestWatcher-Classic.lua:1363
- **Root Cause:** Scheduled timers in `OnEnable()` firing before `EMAModuleInitialize()` completes database setup
- **Solution:** Added `if not EMA.db then return end` safety checks to 8 functions
- **Affected Functions:**
  - `EMAQuestWatcherUpdate()`
  - `CanDisplayQuestWatcher()`
  - `SetQuestWatcherVisibility()`
  - `UpdateUnlockWatcherFrame()`
  - `UpdateHideBlizzardWatchFrame()`
  - `UpdateQuestWatcherDimensions()`
  - `SettingsUpdateBorderStyle()`
  - `SettingsUpdateFontStyle()`
- **Files Modified:** `Modules/QuestWatcher-Classic.lua`
- **Commit:** 5105b0d

#### Issue #2 - Module Load-Order Initialization Errors
- **Problem:** Multiple modules calling `EMAPrivate.Core.isEmaClassicBccBuild()` before Core.lua finished exporting functions
- **Root Cause:** Modules' `OnEnable()` called during addon startup before Core.lua exports complete
- **Solution:** 
  - Moved TrufiGCD check from module-load time to `OnInitialize()` in DisplayTeam
  - Added null/existence checks: `if EMAPrivate.Core and EMAPrivate.Core.isEmaClassicBccBuild and ...`
- **Affected Modules:**
  - `Modules/DisplayTeam.lua`
  - `Modules/Bank.lua`
  - `Modules/Trade.lua`
  - `Modules/Toon.lua`
  - `Modules/Sell.lua`
  - `Modules/Purchase.lua`
- **Commit:** aaac96e

#### Issue #3 - TOC File Configuration
- **Problem:** Addon wasn't loading at all in TBC Anniversary
- **Root Cause:** `EMA.toc` had `## Interface: 100100` (Retail) instead of TBC version
- **Solution:** 
  - Updated `EMA.toc` to interface version `20504` (TBC Anniversary)
  - Created `EMA_TBC.toc` with correct interface
  - Created `ema-tbc-anniversary.toc` to match folder name initially used
- **Why Interface 20504:** Standard for WoW Classic: Burning Crusade Anniversary Edition
- **Commits:** b8c17a6, 7a43888, 7c80688

### Version Branding Updates
- **Updated All TOC Files:**
  - Title: "EMA - TBC Anniversary Fork"
  - Version: "Release-v4.3(0243)-TBC-Anniversary"
  - Author: "Jennifer Calladine 'Ebony/Blossom' | Fork by Bearstonk"
  - Notes: Includes "TBC Anniversary Edition" and fork attribution
- **Updated GUI Locale Strings:**
  - Added fork maintainer attribution: Tom Williams (Bearstonk)
  - Added "[BETA/IN TESTING]" warning in orange
  - Preserved original author attribution
  - Updated copyright to include fork year and maintainer
- **Files Modified:**
  - `EMA.toc`, `EMA_TBC.toc`, `ema-tbc-anniversary.toc`
  - `Locales/Core-Locale-enUS.lua`
- **Commits:** 1a66e2c, 2e2bfd9

### Repository Setup
- **Repository:** `Bearstonk/ema-tbc-anniversary` on GitHub
- **Branch:** `tbc-anniversary` (main development branch)
- **Upstream:** `ebonyfaye/ema` (original repository)
- **Local Development:** `D:\Github\ema-tbc-anniversary`
- **Game Installation:** Symlink at `D:\BlizzardLibrary\World of Warcraft\_anniversary_\Interface\AddOns\EMA`

### Development Workflow Established
1. **Edit:** Make changes in VS Code at `D:\Github\ema-tbc-anniversary`
2. **Test:** Changes immediately available in-game via symlink after `/reload`
3. **Commit:** Git commits with detailed messages
4. **Track:** Document issues in `ISSUES.md`, development notes in this file

---

## Current Status - January 17, 2026

### ✅ Completed
- [x] Fork created from stable base (v4.3(0243))
- [x] Three PRs successfully applied (#142, #143, #144)
- [x] API compatibility layer integrated
- [x] Database initialization timing issues fixed
- [x] Module load-order errors resolved
- [x] TOC files configured for TBC Anniversary (interface 20504)
- [x] Addon loads successfully in-game
- [x] Configuration UI opens with `/ema config`
- [x] Team window displays team members
- [x] Version branding updated with fork attribution
- [x] Development environment configured (symlink, git workflow)

### ⚠️ Known Issues
- [ ] LibBagUtils import errors in multiple modules
- [ ] InterfaceOptions_AddCategory is nil in EMAHelperSettings.lua
- [ ] Various runtime errors from library compatibility (TBC-specific issues)

### 🔄 In Progress
- Testing core functionality (party invites, keybindings, team management)
- Module compatibility verification (11 modules to test)

### 📋 Pending
- Individual module testing (Bank, Follow, Interaction, ItemUse, Macro, Mail, Purchase, Sell, Talk, Toon, Trade)
- Keybinding testing (Team Invite, Disband, Master, Focus F1-F10)
- Performance profiling
- Extended gameplay testing (5+ hours)

---

## Technical Notes

### WoW Classic: Burning Crusade Anniversary Specifics
- **Interface Version:** 20504
- **API Differences from Retail:**
  - No `C_AddOns` namespace - uses global `GetAddOnMetadata()`, `IsAddOnLoaded()`
  - Different library compatibility requirements
  - Classic-era UI framework (pre-10.x changes)

### Architecture Decisions
- **Compatibility Layer Pattern:** Wrapper functions in Core.lua that check for API availability
- **Null Safety Pattern:** Check for `EMAPrivate.Core` and function existence before calling
- **Database Initialization:** Ensure `EMA.db` exists before accessing in all modules
- **Load Order:** Core.lua → Module.lua → Other Core modules → Game modules

### Git Workflow
- **Commit Message Format:** `type: description` (e.g., `fix:`, `feat:`, `docs:`, `chore:`)
- **Detailed Commit Bodies:** Include what changed, why, affected files, and issue references
- **Issue Tracking:** `ISSUES.md` for bug tracking, `DEVLOG.md` for development narrative
- **Branch Strategy:** Currently single `tbc-anniversary` branch (may add feature branches later)

---

## Future Considerations

### Potential Features
- TBC-specific keybindings configuration
- Integration with TBC-Anniversary specific addons
- Performance optimizations for Classic client
- Additional module compatibility fixes as discovered

### Maintenance
- Monitor upstream `ebonyfaye/ema` for critical bug fixes
- Document any additional TBC-specific issues discovered during gameplay
- Consider pull request back to upstream if fixes are universally applicable

### Testing Checklist (from ISSUES.md)
See `ISSUES.md` for comprehensive testing checklist including:
- High priority: Module compatibility (11 modules)
- Medium priority: Keybindings, TBC bindings integration
- Lower priority: Performance profiling, extended testing

---

## References
- **Original Repository:** https://github.com/ebonyfaye/ema
- **Fork Repository:** https://github.com/Bearstonk/ema-tbc-anniversary
- **Base Tag:** Release-v4.3(0243) (commit ef79c96)
- **PRs Applied:** #142 (c5d987b), #143 (90700b9), #144 (e48ffc0)

---

**Last Updated:** January 17, 2026  
**Maintained By:** Tom Williams (Bearstonk)

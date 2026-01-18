# EMA - TBC Anniversary Edition

A specialized fork of **Ebony's MultiBoxing Assistant (EMA)** optimized for **World of Warcraft Classic: Burning Crusade Anniversary Edition**.

**⚠️ BETA / IN TESTING** - This is an independent fork currently undergoing testing.

## Overview

This project maintains EMA at version **4.3(0243)** with targeted improvements and critical bug fixes specifically for TBC Classic gameplay. It includes backported API compatibility fixes from the 0270 development branch to ensure stable operation in Burning Crusade Anniversary.

**Fork Maintainer:** Tom Williams (Bearstonk)  
**Original Author:** Jennifer Calladine (Ebony)

## Project Status

**Current Version:** Release-v4.3(0243)-TBC-Anniversary  
**Base Version:** EMA v4.3(0243)  
**Target Game:** WoW Classic - Burning Crusade Anniversary Edition  
**Status:** Beta - Functional, undergoing module testing  
**Last Updated:** January 17, 2026

### Current State
- ✅ Addon loads successfully
- ✅ Configuration UI functional (`/ema config`)
- ✅ Team management working
- ✅ Core API compatibility layer implemented
- ⚠️ Some library compatibility issues (non-critical)
- 🔄 Module-by-module testing in progress

## What is EMA?

EMA is a comprehensive multiboxing assistant addon that helps players manage multiple characters simultaneously. Features include:

- **Team Management** - Manage characters across your account
- **Party/Raid Coordination** - Sync party invites and raid functions
- **Item Usage** - Auto-use items across your team
- **Quest Tracking** - Synchronized quest tracking
- **Macro Support** - Keybindings for team control
- **Cross-Realm** - Works across connected realms
- **And much more!**

## Why This Fork?

The main EMA codebase has evolved significantly since 4.3(0243). This fork exists because:

1. **Stability** - Version 0243 is a known stable release for Classic TBC
2. **Compatibility** - Includes critical API compatibility fixes for TBC Anniversary
3. **Independence** - Allows focused development for TBC Anniversary specifically
4. **Bug Fixes** - Addresses database initialization and module load-order issues
5. **Maintenance** - Provides a dedicated, tested fork for TBC players

## Key Features in This Version

### PRs Applied from Upstream (v4.3(0270))
This fork includes three critical pull requests backported from the development branch:

- **PR #142** - Core API Compatibility Layer
  - `GetAddOnMetadataCompat()` - Cross-version addon metadata
  - `IsAddOnLoadedCompat()` - Cross-version addon detection
  - Handles C_AddOns namespace (Retail) vs global functions (TBC)

- **PR #143** - DisplayTeam TrufiGCD Integration
  - Updated TrufiGCD addon detection for version compatibility

- **PR #144** - Quest-Classic ElvUI Integration  
  - Updated ElvUI detection for version compatibility

### Critical Bug Fixes (TBC-Specific)
- Fixed database initialization timing in QuestWatcher-Classic
- Fixed module load-order errors (6 modules updated)
- Fixed TOC configuration for TBC Anniversary (interface 20504)
- Added safety checks for Core function availability

### TBC Anniversary Optimizations
- Proper interface version (20504) for TBC Anniversary
- TOC files configured for Classic client
- Module compatibility updates
- Fork attribution visible in UI

## Installation

### Quick Install
1. Download or clone this repository
2. Place the folder in your WoW addons directory:
   ```
   World of Warcraft/_anniversary_/Interface/AddOns/EMA
   ```
3. Restart WoW or type `/reload`
4. Type `/ema config` to access settings

### Development Install (Recommended)
For developers or testers who want live updates:

1. Clone the repository to your development folder:
   ```powershell
   cd D:\Github
   git clone https://github.com/Bearstonk/ema-tbc-anniversary.git
   ```

2. Create a symbolic link (requires administrator privileges):
   ```powershell
   New-Item -ItemType SymbolicLink -Path "D:\BlizzardLibrary\World of Warcraft\_anniversary_\Interface\AddOns\EMA" -Target "D:\Github\ema-tbc-anniversary"
   ```

3. Any edits you make in your git folder will immediately be available in-game after `/reload`

### Verifying Installation
- Open addon list at character select
- Look for **"EMA - TBC Anniversary Fork"**
- Version should show **"Release-v4.3(0243)-TBC-Anniversary"**
- Disable any other EMA versions to avoid conflicts

## Configuration

### First Time Setup
1. Type `/ema config` to open the configuration panel
2. Go to **Team** section
3. Add your characters to the team
4. Set one character as Master
5. Configure keybindings in **Options** section

### Testing Checklist
See [ISSUES.md](ISSUES.md) for comprehensive testing checklist including:
- Core functionality (party invites, team management)
- Module testing (11 modules)
- Keybinding verification
- Performance profiling

## Known Issues

See [ISSUES.md](ISSUES.md) for current bug tracking. Major known issues:

- **LibBagUtils errors** - Some library compatibility issues in TBC (non-critical)
- **InterfaceOptions_AddCategory** - TBC UI framework difference (non-critical)
- Module testing in progress - report any issues you find

## Development

### Branch Structure

- **tbc-anniversary** - Main development branch (based on v4.3(0243))
- Feature branches may be created for specific development work

### Documentation
- **[DEVLOG.md](DEVLOG.md)** - Comprehensive development log with decisions and rationale
- **[ISSUES.md](ISSUES.md)** - Bug tracking and testing checklist  
- **[CHANGELOG.md](CHANGELOG.md)** - Version history and changes
  - Stable, recommended for most users
  - Includes all TBC Anniversary patches

- **master** - Not used; upstream only

## Development History

### Commits in This Fork

1. **8260f47** - Add API compatibility layer for cross-version support
   - Introduces GetAddOnMetadataCompat and IsAddOnLoadedCompat
   - Enables safer API calls across WoW versions

2. **ad5a226** - Update Core.lua to use compatibility functions
   - Refactored Core.lua to utilize new compat wrappers
   - Exports functions for module use

3. **b2d3d42** - Update modules to use API compatibility functions
   - DisplayTeam.lua: TrufiGCD integration fixed
   - Quest-Classic.lua: ElvUI detection fixed

### Base Version

- **ef79c96** (tag: Release-v4.3(0243)) - EMA version 0243
  - Based on Ebony's original v4.3(0243) release
  - Upstream source: https://github.com/ebonyfaye/ema

## Related Forks

This fork was inspired by work from:
- **David-c0degeek/ema** - TBC bindings reference
- Original upstream: **ebonyfaye/ema** (v4.7(0270)+)

## Configuration

After installation:

1. Open the EMA configuration: `/ema config`
2. Navigate to the Team panel
3. Add your characters to the team list
4. Configure party/raid settings
5. Set keybindings in the Keybindings section

## Keybindings

Common multiboxing keybindings available:

- **Team Invite** - Invite all team members to party
- **Team Disband** - Disband current party
- **Set Master** - Set current target as group master
- **Master Follow** - Follow the group master
- **Focus Master** - Focus the group master
- **Target Master** - Target the group master
- **Click to Move** - Toggle auto-interact
- **Custom Focus Keys** - Focus individual team members (F1-F10)

## Troubleshooting

### Addon not loading?
- Check that it's in the correct AddOns folder
- Type `/addons` to see installed addons
- Ensure no Lua errors: `/console scriptErrors 1`

### Team members not syncing?
- Verify all characters are on the same account
- Check that characters are in the same guild or on connected realms
- Review the Team panel configuration

### API errors?
- Ensure you're running on WoW Classic: Burning Crusade Anniversary
- Check the addon for compatibility
- Report issues via GitHub

## Contributing

This is an independent fork maintained for TBC Anniversary. 

**For TBC-specific improvements:**
- Submit issues or PRs to this repository
- Clearly describe the TBC-specific problem or enhancement

**For general EMA improvements:**
- Consider contributing to the upstream: https://github.com/ebonyfaye/ema
- Or maintain patches locally in this fork

## License

All Rights Reserved 2018-2026 Jennifer Calladine (Ebony) and Contributors

EMA includes code from "Jamba" which is Released under the MIT License:
"Jamba" Copyright 2008-2015 Michael "Jafula" Miller

## Support & Documentation

- **Original EMA:** https://github.com/ebonyfaye/ema
- **WoW Classic:** https://classicwow.blizzard.com/
- **Burning Crusade Anniversary:** Part of WoW Classic subscription

## Disclaimer

This fork is independently maintained and is not affiliated with:
- Blizzard Entertainment
- The original EMA author (Ebony)
- WoW Classic development team

Use at your own risk. While stable, multiboxing in WoW should follow Blizzard's Terms of Service.

## Credits

- **Ebony (Jennifer Calladine)** - Original EMA author and maintainer
- **Michael "Jafula" Miller** - Jamba codebase
- **Ace3 Library Team** - Core library infrastructure
- **David-c0degeek** - TBC fork reference
- **Contributors** - Bug reports and suggestions

---

**Happy Multiboxing!** 🎮

For questions or suggestions, feel free to open an issue or pull request.

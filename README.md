# EMA - TBC Anniversary Edition

A specialized fork of **Ebony's MultiBoxing Assistant (EMA)** optimized for **World of Warcraft Classic: Burning Crusade Anniversary Edition**.

## Overview

This project maintains EMA at version **4.3(0243)** with targeted improvements and bug fixes specifically for TBC Classic gameplay. It serves as an independent continuation of EMA for players who want a stable, feature-complete multiboxing addon for Burning Crusade Anniversary.

## Project Status

**Current Version:** Release-v4.3(0243)-TBC-Anniversary  
**Base Version:** EMA v4.3(0243)  
**Target Game:** WoW Classic - Burning Crusade Anniversary Edition  
**Last Updated:** January 17, 2026

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
2. **Compatibility** - Maintains compatibility with TBC Classic gameplay and APIs
3. **Independence** - Allows focused development for TBC Anniversary specifically
4. **Maintenance** - Provides a dedicated fork for TBC players

## Key Features in This Version

### API Compatibility Layer (Added)
- **GetAddOnMetadataCompat()** - Cross-version addon metadata retrieval
- **IsAddOnLoadedCompat()** - Cross-version addon detection
- Supports: Classic, TBC, Wrath, Cata, and Retail WoW

### TBC-Specific Optimizations
- DisplayTeam module updated for TBC compatibility
- Quest-Classic module integration
- Bindings_TBC.xml for TBC keybindings

### Cross-Version Support
While optimized for TBC, this version includes compatibility code that may work on:
- WoW Classic (Vanilla)
- Classic Wrath
- Classic Cata
- Modern Retail (partial support)

## Installation

1. Clone or download this repository
2. Rename the folder to `EMA` if needed
3. Place it in your WoW addons folder:
   ```
   World of Warcraft/_retail_/Interface/AddOns/EMA
   ```
   or for Classic:
   ```
   World of Warcraft/_classic_bcc_/Interface/AddOns/EMA
   ```
4. Restart WoW or type `/reload`
5. Type `/ema config` to access settings

## Branch Structure

- **tbc-anniversary** - Main development branch (based on v4.3(0243))
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

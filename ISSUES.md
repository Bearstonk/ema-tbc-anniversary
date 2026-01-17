# Issues & To-Do List

## Active Issues

### High Priority

- [ ] **Test addon loading in TBC Classic**
  - Load addon in WoW Classic: Burning Crusade Anniversary
  - Check for Lua errors in `/console scriptErrors 1`
  - Verify no taint issues
  - Status: Not started

- [ ] **Verify Party/Raid Functionality**
  - Test party invite system with multiple characters
  - Test raid conversion (5+ members)
  - Verify all team members receive invites
  - Test disband functionality
  - Status: Not started

- [ ] **Test All Keybindings**
  - Test Team Invite keybinding
  - Test Team Disband keybinding
  - Test Master/Focus keybindings (F1-F10)
  - Test Follow/Assist keybindings
  - Status: Not started

- [ ] **Module Compatibility Testing**
  - [ ] Bank.lua - Test bank operations sync
  - [ ] Follow.lua - Test follow mechanics
  - [ ] Interaction.lua - Test NPC interactions
  - [ ] ItemUse.lua - Test item sync
  - [ ] Macro.lua - Test macro execution
  - [ ] Mail.lua - Test mail operations
  - [ ] Purchase.lua - Test vendor purchases
  - [ ] Sell.lua - Test item selling
  - [ ] Talk.lua - Test quest dialogue
  - [ ] Toon.lua - Test character management
  - [ ] Trade.lua - Test trade window
  - Status: Not started

### Medium Priority

- [ ] **Integrate TBC Bindings**
  - Evaluate David-c0degeek's Bindings_TBC.xml
  - Compare with current Bindings.xml
  - Integrate if provides value
  - Test all bindings work
  - Status: Pending

- [ ] **Create TROUBLESHOOTING Guide**
  - Document common TBC-specific issues
  - Add solutions
  - Include debug tips
  - Status: Not started

- [ ] **Performance Profiling**
  - Test on various system specs
  - Check memory usage
  - Monitor CPU during multiboxing
  - Optimize if needed
  - Status: Not started

- [ ] **Settings Persistence**
  - Verify team list saves
  - Verify keybindings persist
  - Verify UI settings save
  - Test after game restart
  - Status: Not started

### Lower Priority

- [ ] **UI Polish**
  - Test on different resolutions
  - Verify text scaling
  - Check tooltip display
  - Test dark/light UI options
  - Status: Not started

- [ ] **Cross-Realm Testing**
  - Test with characters on different realms
  - Verify realm-specific functionality
  - Test with realm-connected realms
  - Status: Not started

- [ ] **Documentation Updates**
  - Add TBC-specific configuration guide
  - Document any workarounds
  - Update FAQ
  - Status: Not started

## Feature Requests

- [ ] Add TBC-specific quest tracking features
- [ ] Consider TBC-specific macro templates
- [ ] Add reputation tracking for TBC factions
- [ ] Consider addon config export/import
- [ ] Add character-specific settings profiles

## Bug Reports

*Submit new bug reports as you find them*

### Template
```
**Title:** [Brief description]
**Game Version:** WoW Classic - Burning Crusade Anniversary
**Steps to Reproduce:**
1. ...
2. ...
3. ...

**Expected Behavior:**
[What should happen]

**Actual Behavior:**
[What actually happens]

**Addon Version:** 4.3(0243)
**Lua Errors:** [Any console errors]
```

## Version Tracking

- **Current Version:** Release-v4.3(0243)-TBC-Anniversary
- **Last Tested:** Not yet
- **Last Updated:** January 17, 2026

## Testing Checklist

### Before Release
- [ ] All High Priority issues resolved
- [ ] At least 5 hours of gameplay testing
- [ ] No Lua errors in console
- [ ] All core modules tested
- [ ] Keybindings functional
- [ ] Settings persist across sessions
- [ ] Version number updated
- [ ] CHANGELOG updated
- [ ] README accurate

### Release Steps
- [ ] Tag release in git
- [ ] Update version in EMA.toc
- [ ] Create GitHub release
- [ ] Update CHANGELOG

---

## How to Contribute

Found an issue? Have an idea?

1. **Check this list** - Your issue might already be tracked
2. **Create an issue** - Be specific with steps to reproduce
3. **Submit a PR** - With your fix or improvement
4. **Test thoroughly** - Before marking as resolved

---

**Last Updated:** January 17, 2026  
**Maintained by:** Bearstonk

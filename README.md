LibCombatLogging
==========================
This library can be used to play nice with other combat logging addons.

# API

- `CL.IsLogging(addon) => boolean`
- `CL.GetNumLogging() => number`
- `CL.GetLoggingAddOns(excludeAddon) => string|nil`
- `CL.StartLogging(addon) => boolean`
- `CL.StopLogging(addon) => boolean`
- `CL.LoggingCombat(addon, newstate) => boolean, number`

## CallbackHandler-1.0

You can find information how these API's work in the [wowace project page](https://www.wowace.com/projects/callbackhandler).

- `CL.RegisterCallback(addonRef, event, method, ...)`
- `CL.UnregisterCallback(addonRef, event)`
- `CL.UnregisterAllCallbacks(addonRef)`

## Variables

- `events` type is one of the values in `CL.CallbackEvents`:
  - `STARTED_LOGGING`
  - `STOPPED_LOGGING`
  - `ADDON_STARTED_LOGGING`
  - `ADDON_STOPPED_LOGGING`
- `addon` and `excludeAddon` is a unique `string` that is required for starting and stopping logging.
- `newstate` is a `boolean` to represent logging being enabled or disabled. if ommited you instead get the logging state.

# Example

A example wrapper you can place on top of your addon file to swap out the default `LoggingCombat` API with the library provided one, and still use the API as you previously had in your code:

```lua
local addonName = ...
local CL = LibStub("LibCombatLogging-1.0") ---@type LibCombatLogging
local LoggingCombat = function(...) return CL.LoggingCombat(addonName, ...) end
```

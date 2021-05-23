LibCombatLogging
==========================
This library can be used to play nice with other combat logging addons.

# API

`CL.RegisterCallback(callback, ...events)`

`CL.UnregisterCallback(callback, ...events)`

`CL.IsLogging(addon) => boolean`

`CL.GetNumLogging() => number`

`CL.GetLoggingAddOns(excludeAddon) => string|nil`

`CL.StartLogging(addon) => boolean`

`CL.StopLogging(addon) => boolean`

`CL.LoggingCombat(addon, newstate) => boolean, number`

## events

You can find all the valid events in the table `CL.CallbackEvents`. They are `STARTED_LOGGING`, `STOPPED_LOGGING`, `ADDON_STARTED_LOGGING`, and `ADDON_STOPPED_LOGGING`.

## addon
## excludeAddon

The addon parameter is a unique handle you can use in your addon when querying or starting/stopping logging.

## newstate

If provided the logging will start/stop, depending if it's `true` or `false`, and if you omit this parameter you simply get the active logging state.

# Example

A example wrapper you can place on top of your addon file to swap out the default `LoggingCombat` API with the library provided one, and still use the API as you previously had in your code:

```
local addonName = ...
local CL = LibStub("LibCombatLogging-1.0") ---@type LibCombatLogging
local LoggingCombat = function(...) return CL.LoggingCombat(addonName, ...) end
```

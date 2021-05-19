LibCombatLogging
==========================
This library can be used to play nice with other combat logging addons.

# API

`CL.IsLogging(addon)`

`CL.GetNumLogging()`

`CL.StartLogging(addon)`

`CL.StopLogging(addon)`

`CL.LoggingCombat(addon, newstate)`

## addon

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

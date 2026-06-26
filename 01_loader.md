# 01 - Spot the LuaObfusactor loader

The sample starts with a long `local v0 = tonumber; local v1 = string.byte; ...` block, which is characteristic of LuaObfusactor-style wrapping.

That pattern usually means the file is not the real source yet. Instead, it is a custom virtual machine or bytecode loader that:

- hides common Lua primitives behind local aliases,
- stores the real payload in a compact encoded string,
- decodes that string at runtime, then
- executes the decoded chunk with `loadstring`.

In this sample, the giveaway is the `LOL!` payload marker near the end of the script.

## What to look for

- `loadstring`
- `HttpGet`
- `v15("LOL!...")`
- repeated `local vN` aliases

Once you find the marker, the next step is to extract and decode the embedded string.

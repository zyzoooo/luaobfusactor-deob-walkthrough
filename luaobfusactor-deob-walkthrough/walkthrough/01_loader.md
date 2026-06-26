# 01 - Spot the LuaObfusactor loader

The sample starts with a long chain of locals like:

`local v0 = tonumber; local v1 = string.byte; local v2 = string.char ...`

This is not normal Lua style. It is a classic LuaObfusactor pattern used to flatten readability and hide standard library usage behind renamed references.

At this stage, the file is not the real logic yet. It is a loader layer.

## What this layer is doing

This wrapper typically exists to:

- Rename core Lua functions into short local variables
- Break static analysis by removing obvious function calls
- Store the actual payload in an encoded string
- Reconstruct and execute the payload at runtime

So instead of seeing logic directly, you are looking at a controlled decoder.

## Execution flow (what actually happens)

1. Local aliases are created for Lua functions
2. The script defines helper functions for decoding
3. An encoded string is stored (usually large and unreadable)
4. That string is transformed back into Lua code
5. The result is passed into `loadstring` or an equivalent execution function

At runtime, this file behaves like a loader, not a script.

## Key indicator in this sample

The biggest giveaway is the `LOL!` marker embedded near the end of the script.

That marker is typically used as a delimiter for the encoded payload section in LuaObfusactor outputs.

Once you see that, everything above it is just setup logic.

## What to look for

Focus on these patterns:

- `loadstring`
- `HttpGet` or external fetch calls
- `v15("LOL!...")` or similar wrapper calls
- long encoded strings (base64-like or custom encoded blobs)
- repeated `local vN` variable aliasing

## Next step

Once the `LOL!` payload section is found, the goal is to:

- extract the encoded string cleanly
- identify the decoding function used
- manually replicate or simplify the decoder
- print or dump the final decoded output instead of executing it

That decoded output is the real script

# 04 - Rebuild the source

At this stage, the work is no longer extraction. It is reconstruction.

You already have:
- the decoded payload
- the string map
- the feature layout
- the execution patterns

Now the goal is to rebuild readable Lua that matches the original behavior without the obfuscation noise.

## How reconstruction is done

This step is a structured rewrite, not interpretation.

You:

- replace anonymous locals (`v1`, `v2`, etc.) with meaningful names based on usage
- group UI construction into logical sections (tabs, frames, toggles)
- isolate repeated logic into reusable helper functions
- separate gameplay automation from utility features
- map string constants directly to their functional blocks
- preserve runtime behavior while removing obfuscation layers

## What the final structure becomes

After cleanup, the script usually resolves into:

- UI layer (menus, toggles, buttons)
- feature modules (Auto Farm, Auto Race, Auto Drive)
- utility systems (FPS Booster, Anti AFK)
- networking / teleport logic
- key system validation

At this point, the original obfuscation is fully irrelevant. Only behavior matters.

## Output

The reconstructed version of the script is saved as:

artifacts/reconstructed.lua


This file represents the cleaned, readable equivalent of the original payload.

## Good repository practice

For a clean and useful walkthrough repository, include:

- original obfuscated sample (`samples/` or external reference)
- decoding / extraction scripts
- payload extraction stage
- string analysis stage
- reconstructed output
- short explanation per stage (like this repo does)

## Result

A fully obfuscated script is reduced into structured, readable logic that matches its actual runtime behavior without the obfuscation layer

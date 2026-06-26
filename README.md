# Lua Obfuscation Deobfuscation Walkthrough

This repo shows how obfuscated Lua gets broken down step by step into clean readable code. No guesswork. Just straight reverse engineering.

## Purpose

I built this to demonstrate how Lua obfuscation actually falls apart when you know what you are doing.

Most obfuscation is not as strong as it looks once you start tracing it properly.

## Structure

 ``` example/
    original_obfuscated.lua

  walkthrough/
    01_overview.md
    02_analysis.md
    03_deobfuscation.md
    04_cleanup.md
```

## How to use

Start at `walkthrough/01_overview.md` and follow it in order.

Keep the original script open from `example/original_obfuscated.lua` so you can see exactly what is being broken down.

## What you will see here

- How obfuscation tricks get exposed
- How execution flow is actually tracked
- How encoded strings get pulled apart
- How messy code gets turned readable
- How fast most “secure” Lua falls apart

## Credits

zyzo

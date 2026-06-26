# 03 - Build a string map

After decoding a LuaObfusactor sample, the quickest way to understand the script is to extract readable strings.

In this sample, the constants immediately reveal the shape of the script:

- `Midnight Chasers`
- `Key System`
- `Auto Farm`
- `Auto Race`
- `Auto Drive`
- `No Rubble`
- `Anti AFK`
- `FPS Booster`
- `Server Hop`

That tells you the program is a Roblox UI script with gameplay toggles, quality-of-life features, and a key gate.

## Helper script

`scripts/extract_strings.js` prints printable strings found in the decoded chunk.

```bash
node scripts/extract_strings.js artifacts/decoded.luac
```

This step is where the high-level behavior becomes obvious.

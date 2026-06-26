# 03 - Build a string map

Once the payload has been decoded, the fastest way to understand what the script actually does is to stop looking at structure and start extracting human-readable strings.

At this stage, control flow and logic are still noisy, but strings act as anchors. They expose intent immediately.

## What the strings reveal

In this sample, the extracted constants clearly outline the script’s purpose:

- `Midnight Chasers`
- `Key System`
- `Auto Farm`
- `Auto Race`
- `Auto Drive`
- `No Rubble`
- `Anti AFK`
- `FPS Booster`
- `Server Hop`

These are not random labels. They define the full feature set of the script.

At this point, you already understand the script’s *behavior*, even before touching the logic.

## Why this step matters

Obfuscated Lua often hides structure, but it rarely hides intent.

Strings bypass:

- renamed variables
- virtual machine layers
- control flow flattening

They give you a direct view of what the script was designed to do.

## Helper script

The following tool extracts printable strings from the decoded payload:

```bash
node scripts/extract_strings.js artifacts/decoded.luac
``` id="7nqk3d"

## Output usage

Use the output to:

- map features to functions later in the code
- locate UI construction blocks
- identify key validation logic
- find remote calls tied to specific features

This step turns an unreadable blob into a functional feature list

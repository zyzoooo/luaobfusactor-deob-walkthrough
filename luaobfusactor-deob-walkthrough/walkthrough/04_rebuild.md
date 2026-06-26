# 04 - Rebuild the source

At this point, the job is translation rather than guessing.

Use the string map and the control-flow clues to rebuild readable Lua:

- replace anonymous locals with named services and state,
- group UI elements into tabs,
- move repeated vehicle logic into helper functions,
- isolate the anti-AFK, FPS, teleport, and routing behaviors,
- keep the reconstructed script faithful to the observed constants.

The finished result in this repo is `artifacts/reconstructed.lua`.

## Good repo practice

For a GitHub demo, it helps to include:

- the original sample in a `samples/` folder or as an external download,
- the decoder script,
- the string extraction step,
- the reconstructed output,
- and short writeups for each phase.

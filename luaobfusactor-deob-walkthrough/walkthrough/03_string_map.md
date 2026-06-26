# 03 - Build a String Map

After decoding the payload, you are still not looking at clean logic yet.

At this stage, the fastest way to understand the script is not by reading code, but by extracting **strings**.

Strings act like labels. They reveal intent even when everything else is still obfuscated.

---

## What strings show immediately

In this sample, extracted strings already reveal the full feature set:

- `Midnight Chasers`
- `Key System`
- `Auto Farm`
- `Auto Race`
- `Auto Drive`
- `No Rubble`
- `Anti AFK`
- `FPS Booster`
- `Server Hop`

---

## What this tells you

Even without understanding the code, you can already classify the script:

### 1. It is feature-based
Each string represents a toggle or system:

- automation features (Auto Farm, Auto Race, Auto Drive)
- utility features (FPS Booster, Anti AFK)
- navigation features (Server Hop)
- game-specific modifications (No Rubble)

---

### 2. It uses a gated system
`Key System` strongly indicates access control before features can run.

---

## Why this step is powerful

Obfuscation hides structure, but it rarely hides intent.

Strings bypass:

- variable renaming
- control flow flattening
- encoding layers

They remain visible because the script needs them for UI and logic.

---

## Beginner insight

At this point:

You do NOT know how the script works internally.

But you already know:

- what it does
- what features exist
- how it is structured at a high level

That alone is enough to understand most of the program.

---

## Helper script

This step uses string extraction from the decoded payload:

```bash
node scripts/extract_strings.js artifacts/decoded.luac
```

---

## What to do with the output

Use the strings to:

- map features to code sections later
- identify UI building blocks
- locate key system logic
- find function names tied to features

---

## Key idea

Strings turn an unreadable binary into a feature list.

That feature list becomes your roadmap for the final rebuild.

# 02 - Extract the LuaObfusactor Payload

Once the loader is identified, the next step is isolating the real encoded data hidden inside it.

This is where the actual script is stored, but it is still not readable yet.

---

## Where the payload is found

In most LuaObfusactor samples, the payload appears after a marker such as:

```text
LOL!
```

Everything before this is setup code. Everything after is encoded data.

---

## What the payload actually is

The payload is a single long string that represents the real script in a hidden format.

It is usually:

- hex encoded data
- repeat-compressed bytes
- or mixed encoding (both together)

---

## How decoding works (simple breakdown)

You do NOT need to guess anything. The format is consistent.

### Step 1 - isolate payload
Remove everything before and including the `LOL!` marker.

---

### Step 2 - read sequentially
Process the remaining string from left to right.

---

### Step 3 - interpret chunks

There are two main patterns:

#### Hex mode
Pairs of characters represent bytes:

```text
4F = 79
2A = 42
```

Each pair becomes one byte.

---

#### Repeat mode
Some sequences indicate repetition:

```text
XQ
```

Meaning:
- `X` = repeat count
- `Q` = trigger for repeating the previous decoded byte

This allows compression of repeated values.

---

### Step 4 - build output
All decoded bytes are appended into a buffer.

This produces the real payload data.

---

## What you get after decoding

Even after this step, you usually do NOT get readable Lua.

Instead, you get one of:

- Lua bytecode (`luac`)
- another encoded layer
- or a second-stage loader

---

## Key idea

This step does not reveal logic.

It only removes the first layer of hiding.

---

## Helper script

A script can automate this process:

```bash
node scripts/extract_payload.js path/to/pasted-text.txt artifacts/decoded.luac
```

---

## Output warning

The result will often look like garbage in a text editor.

That is expected.

It is raw byte data, not readable Lua.

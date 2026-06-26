# 02 - Extract the LuaObfusactor payload

At this stage, the loader has already been identified and the next step is isolating the actual encoded payload hidden inside it.

LuaObfusactor typically stores the real script in a compact repeat-based + hex-encoded stream. It is not random encoding. It follows a strict pattern designed to compress and disguise bytecode.

## How the encoding works

The payload begins immediately after the `LOL!` marker and is processed sequentially.

The decoding logic works like this:

1. Remove everything before and including the `LOL!` marker
2. Read the remaining string from left to right in chunks
3. Each chunk is interpreted in one of two ways:

### Repeat mode
- If a character pair matches the pattern `XQ`:
  - `X` is treated as a repeat count (usually a single hex character or digit)
  - The last decoded byte is repeated `X` times

### Hex mode
- Otherwise, each pair is treated as a hex byte
- The pair is converted into a single byte value

4. Repeat state persists until a new hex byte is decoded
5. All decoded bytes are appended to reconstruct the final buffer

## What this produces

The output is not readable Lua yet.

It is usually one of the following:

- Lua bytecode (`luac` output)
- A second-stage loader
- A compressed or packed chunk that still requires `loadstring` or `load`

So even after decoding, execution logic is not fully revealed yet.

## Helper script

The script below replicates the decoding process and extracts the raw payload automatically:

```bash
node scripts/extract_payload.js path/to/pasted-text.txt artifacts/decoded.luac
``` id="8wqk2p"

## Output

The resulting file will appear as binary Lua bytecode.

It will look corrupted or unreadable in a text editor. That is expected.

Do not treat it as text.

It must be passed into a Lua VM or further unpacked depending on the next stage of obfuscation.

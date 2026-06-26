# 02 - Extract the LuaObfusactor payload

LuaObfusactor wraps the payload in a simple repeat-plus-hex encoding.

The decoder logic is:

1. Skip the `LOL!` prefix.
2. Read the payload two characters at a time.
3. If the second character is `Q`, treat the first character as a repeat count.
4. Otherwise, interpret the pair as a hex byte.
5. If a repeat count is pending, repeat the decoded byte that many times.

That is enough to recover the decoded Lua chunk.

## Helper script

`scripts/extract_payload.js` performs the same logic and writes the decoded bytes to a file.

```bash
node scripts/extract_payload.js path/to/pasted-text.txt artifacts/decoded.luac
```

The output is binary Lua bytecode, so it will look garbled in a text editor.

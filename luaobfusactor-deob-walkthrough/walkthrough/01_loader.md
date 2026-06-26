# 01 - Spot the LuaObfusactor Loader

The first step is recognizing that the file is not the real script yet.

What you are looking at is a **loader layer**, not actual gameplay or logic.

---

## What it looks like

You will usually see something like:

```lua
local v0 = tonumber
local v1 = string.byte
local v2 = string.char
local v3 = string.sub
...
```

At first glance it looks messy, but it is very structured.

---

## What this layer actually is

This section is a **setup environment** created by LuaObfusactor.

It exists to:

### 1. Rename Lua functions

Core Lua functions get shortened into meaningless variables:

- `string.byte` → `v1`
- `string.char` → `v2`
- `tonumber` → `v0`

This removes readability on purpose.

---

### 2. Break static reading

Instead of seeing:

```lua
string.sub
```

You only see:

```lua
v3
```

So you cannot easily understand what is being used.

---

### 3. Prepare decoding tools

These renamed functions are reused later to decode hidden data.

So this section is basically building a “toolkit” for the rest of the script.

---

## How to instantly recognize it

You are still in the loader if you see:

- many `local vN = ...`
- no real game or UI logic
- no visible functions like `AutoFarm` or `UI`
- long encoded strings near the bottom
- execution calls like `loadstring`

---

## Key idea

If you are seeing this section:

You are NOT at the real script yet.

You are only at the **mask layer** that hides it.

---

## What comes next

After this section, the script will usually contain:

- an encoded payload
- a marker like `LOL!`
- or a large compressed string

That is where actual decoding begins.

# Pointring++

# Pointring++

**Pointring++** (**Po**int + **int** + st**ring** + **++**) is a custom-designed esoteric encoding language and **Luau obfuscator** built for Roblox. 

Instead of relying on standard Base64 or typical byte-array encodings, Pointring++ translates source code into structured sequences of dots (`.`), grouped expansions (`(...)`), and null markers (`()`), wrapping the output in a single-line, fragmented loader with anti-tamper checks.

---

## 🧠 How the Language Works

Pointring++ converts characters into numerical positions and represents them visually through dot counts:

* **`1` to `9` (Points):** Represented directly by the number of dots (e.g., `.` = 1, `...` = 3, `.........` = 9).
* **`10+` (`+` Expansion):** Any value greater than 9 is enclosed in parentheses (e.g., `(............)` = 12).
* **`0` (Zero):** Represented by empty parentheses `()`.
* **Line Breaks (`\n`):** Represented by triple null markers `()()()`.
* **`++` Extended Charset:** Full UTF-8 support including uppercase/lowercase letters, numbers, accents, and Lua/Luau syntax symbols (`[]~{},.:;/?°-+=§\|!@#$%&*()"'_<>^`).

### Example
```text
Input:  1 + 1 = 2
Output: (......................................................) (....................................................................................................................................................) (...............................................................................................................................) (....................................................................................................................................................) (......................................................) (....................................................................................................................................................) (................................................................................................................................) (....................................................................................................................................................) (.......................................................)
```

---

## 🛡️ Obfuscator Features

* **Two-Layer Runtime Decoding:** Reconstructs dots into integer arrays first, then maps integers back into executable Luau source code in memory.
* **Payload & Dictionary Fragmentation:** Splits both the character table and the encoded dot payload into dozens of scattered variables across a single minified line.
* **Junk Code & Decoy Injection:** Embeds dead-code branches and fake dot strings (`'(.......) .. ...'`) to disrupt static analysis and manual reading.
* **Roblox Environment Verification:** Validates `DataModel`, `RunService`, and C-closure integrity via `debug.info` to prevent execution or `loadstring` hooking outside the Roblox engine.

---

## 🚀 Usage (Roblox Studio)

1. Enable **`LoadStringEnabled`** on `ServerScriptService` in your Roblox Studio place (required for runtime execution on the server).
2. Open the generator script (`PointringGenerator.lua`) and paste your target code inside the `meuScript` variable.
3. Run the generator in Roblox Studio's **Command Bar** or a temporary Script.
4. Copy the single-line obfuscated output from the **Output** window.

---

## ⚠️ Disclaimer

This project was created for educational purposes, code protection, and exploring custom esoteric encoding systems in Luau. Always keep your original source code backed up safely.

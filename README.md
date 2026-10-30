# BIP-39 12th Seed Word Recovery & Calculator (100% Offline)

A fast, lightweight, and completely standalone tool to calculate all mathematically valid candidates for the **12th word** of a BIP-39 mnemonic seed phrase when the first **11 words** are known.

Live GitHub Pages: **https://dikanevn.github.io/last-seed-word/**

---

## 🔒 Security & Golden Offline Rule

> **CRITICAL RULE:** Never enter real recovery seed phrases on any device connected to the internet!

This utility is deliberately built to run 100% locally with **zero network requests** and zero external dependencies:

1. **Option 1 (Direct via Browser):**
   - Open the live page on GitHub Pages: `https://dikanevn.github.io/last-seed-word/`
   - **Disconnect your internet connection** (turn off Wi-Fi or unplug ethernet). The page UI will switch to the green `OFFLINE MODE (SECURE)` status indicator.
   - Enter your 11 words and inspect the valid candidates. All SHA-256 checksum computations execute entirely inside your local browser via native `crypto.subtle.digest`.
   - Close the browser tab before reconnecting to the internet.

2. **Option 2 (Air-gapped PC / Maximum Security):**
   - Download the standalone [`index.html`](index.html) file (press `Ctrl+S`).
   - Copy `index.html` to a clean USB flash drive.
   - Open and run `index.html` on a permanently air-gapped machine with no network interfaces.

---

## ⚙️ Mathematical Background

- The standard BIP-39 English dictionary contains 2048 words (`2^11`). Each word represents an 11-bit index.
- 11 words encode: `11 words * 11 bits = 121 bits`.
- A 12-word mnemonic phrase consists of 128 bits of entropy + 4 bits of checksum (`128 + 4 = 132 bits = 12 * 11 bits`).
- The 4-bit checksum is defined as the first 4 bits of the SHA-256 hash of the 128-bit entropy.
- The 12th word contains the remaining **7 bits of entropy** (`128 - 121 = 7 bits`) and the **4 bits of checksum**.
- Because 7 bits provide `2^7 = 128` possible states, and each state yields exactly one valid 4-bit SHA-256 checksum, there are always **exactly 128 mathematically valid candidates** for the 12th word out of the 2048-word dictionary for any combination of 11 words.

---

## ✨ Features

- **100% Offline & Self-Contained:** The full 2048-word BIP-39 list and SHA-256 logic are embedded directly into a single `index.html` file.
- **Dynamic Network Monitor:** Visual status badge alerts you if the network connection is active or disconnected.
- **Smart Inputs & Autocomplete:** Real-time validation and prefix suggestions for all BIP-39 words.
- **Quick Paste:** Paste all 11 words separated by whitespace directly into the quick paste area.
- **One-Click Copy:** Click any candidate word to copy the complete 12-word recovery phrase directly to your clipboard.
- **Zero Dependencies:** Pure HTML/CSS/JavaScript with zero third-party CDNs, fonts, or tracking scripts.

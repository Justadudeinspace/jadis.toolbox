# Jadis Toolbox 🛠️

A personal collection of **custom scripts and tools** designed to streamline development, automate workflows, and maintain system snapshots. This repository is curated and maintained by JADIS — built for clarity, efficiency, and transparency.

---

## 🗂 Repository Structure

```text
/jadis.toolbox
├── scripts/
│   ├── master_log/       # Termux one-tap system snapshot scripts
│   │   └── take-master_log.sh
│   ├── utilities/        # Miscellaneous helpers (Coming Soon)
│   └── experimental/     # Work-in-progress scripts (Coming Soon)
├── docs/                 # Documentation and notes (Coming Soon)
└── README.md             # This front page
```

---

## ⚡ Key Scripts

`take-master_log.sh`

Purpose: One-tap snapshot of your system and `$HOME` folder in Termux.

### Features:

Tree-style file snapshot of `$HOME` (or fallback to find if tree isn’t installed)

Captures system logs: logcat, battery info, running processes, and network checks

Appends summary into a persistent master.log

Handles unrooted devices gracefully


### Usage:

1. Place in `~/.shortcuts` for Termux Widget access.


2. Make executable:
```bash
chmod +x ~/.shortcuts/take-master_log.sh
```

3. Tap to run. Snapshots will be saved to `~/storage/shared/logs/`.





---

## Other Scripts

utilities/ — (Coming Soon) Small helpers for repetitive tasks like file cleanup, environment setup, or temporary logs.

experimental/ — (Coming Soon) Scripts under testing; may be unstable or incomplete.



---

## 🛠 Installation / Setup

1. Clone the repo:
```git
git clone https://github.com/Justadudeinspace/jadis.toolbox.git
```

2. Optional: Set up Termux permissions:
```bash
# Check /scripts/*/README.md's for individual scripts required deps
termux-setup-storage
pkg install termux-api
```

3. Make scripts executable:
```bash
chmod +x scripts/*/*.sh
```



---

## 📜 Conventions & Notes

Scripts are self-contained where possible — no hidden dependencies.

Log outputs are centralized in `~/storage/shared/logs/`.

Scripts are designed to fail gracefully when commands aren’t available or permissions are restricted.

All personal scripts are tagged in the repo for easier navigation.



---

## 🔗 Useful Links

Termux Widget Setup

Termux API Package



---

# ⚖️ License

MIT License

> - This toolbox is personal use / experimentation. Feel free to adapt scripts for your own workflow, but consider crediting JADIS if shared publicly.


---

# Jadis Toolbox 🛠️

> - A personal collection of custom scripts and tools designed to streamline development, automate workflows, and maintain system snapshots. Curated and maintained by JADIS, this toolbox is built for clarity, efficiency, and transparency.


---

## 🗂 Repository Structure

```lsd
/jadis.toolbox
├── scripts/
│   ├── master_log/       # Termux one-tap system snapshot scripts
│   │   └── take-master_log.sh
│   ├── github_backup/    # Encrypted GitHub backup scripts
│   │   └── github_backup.sh
│   ├── newproject/       # Project bootstrapper scripts
│   │   └── newproject.sh
│   ├── timelog/          # Enhanced CLI time tracking
│   │   └── timelog.sh
│   ├── utilities/        # Miscellaneous helpers (Coming Soon)
│   └── experimental/     # Work-in-progress scripts (Coming Soon)
├── docs/                 # Documentation and notes
│   ├── termux-llm-vulcan.md
│   └── termux-venv.md
└── README.md             # This front page
```

---

## ⚡ Key Scripts

### take-master_log.sh

Purpose: One-tap snapshot of your system and $HOME folder in Termux.

Features:

Tree-style snapshot of $HOME (or fallback to find if tree isn’t installed)

Captures system logs: logcat, battery info, running processes, and network checks

Appends summary into a persistent master.log

Handles unrooted devices gracefully


Usage:

```
# Place script in ~/.shortcuts for Termux Widget access
chmod +x ~/.shortcuts/take-master_log.sh

# Run manually
bash ~/.shortcuts/take-master_log.sh

Snapshots saved to:

~/storage/shared/logs/
# Files: master-log-battery.json, master-log-logcat.log, master-log-ping.log, master-log-ps.log, master-log-tree.log, master.log
```

---

### timelog.sh — Enhanced CLI Time Tracker

Purpose: Track work sessions, calculate durations, link sessions, and generate invoices.

Quickstart:
```
chmod +x timelog.sh
./timelog.sh start "Project Alpha" "Initial setup"
./timelog.sh stop "Wrapped up task A"
./timelog.sh status
./timelog.sh invoice "Project Alpha" ~/invoice.txt
```
Config:
```
export TIMELOG_CONFIG="$HOME/.my_custom_timelog_config"
export TIMELOG_DIR="$HOME/Documents/my_timelogs"
```
Or use a config file at:
```
~/.config/timelog/timelog.conf
```
CSV Log Format:

Date, Project, Action, Time, Full Timestamp, Timezone, SessionID, Info, User, Duration


---

### newproject.sh — Project Bootstrapper

Purpose: Create project scaffolds, initialize git, apply licenses, and optionally create GitHub repos.

Quickstart:
```
./newproject.sh my-awesome-project
./newproject.sh -d "ML project" -t python ml-project
./newproject.sh -g -u "Jane Doe" -e "jane@example.com" awesome-repo
```
Options:
```
-d, --description Project description

-l, --license License (MIT, GPL-3.0, Apache-2.0, BSD-3-Clause, None)

-t, --type Project type: python, node, bash, web, general

-u, --user Git username

-e, --email Git email

-g, --github Create GitHub repo (requires gh)

-n, --no-commit Skip initial commit
```

Environment Variables:
```
export PROJECTS_DIR="$HOME/projects"
export DEFAULT_GIT_USER="Your Name"
export DEFAULT_GIT_EMAIL="you@host.example"
export DEFAULT_LICENSE="MIT"
export CREATE_GITHUB_REPO=1
```

---

### github_backup.sh — Encrypted GitHub Backup

Purpose: Backup local folders to private GitHub repos with optional git-crypt encryption.

Quickstart:
```
chmod +x github_backup.sh
./github_backup.sh ~/Documents mydocs-backups
```
Advanced:

Auto-create repo using AUTO_CREATE_REPO=1 and GITHUB_TOKEN

Pre/Post backup hooks available

Retention of newest backups with MAX_LOCAL_BACKUPS


> Always securely store your git-crypt key. Losing it means losing access to encrypted backups.




---

## 🧭 Termux Virtual Environment & LLM Setup

- Virtual Environment:
```
pkg install python
python -m venv .venv
source .venv/bin/activate
```
Test:
```
python -m pip install requests
python -c "import requests; print('Venv OK ✅')"
```
- LLM with Vulkan (Termux-LLM-Vulcan):

Install Vulkan deps: `pkg install vulkan-tools shaderc`

Install Vulkan driver and verify with vulkaninfo

Build llama.cpp with Vulkan support

Load GGUF model (DeepSeek-R1-Distill-Qwen-1.5B-Q4_K_M.gguf)



---

## 📜 Conventions & Notes

Scripts are self-contained and fail gracefully

Logs centralized in `~/storage/shared/logs/`

Designed for unrooted devices

Environment variables preferred for configuration



---

## 🔗 Useful Links

[Termux Widget Setup](https://wiki.termux.com/wiki/Termux:Widget)

[Termux API Package](https://wiki.termux.com/wiki/Termux:API)

[llama.cpp Vulkan Build Documentation](https://github.com/ggerganov/llama.cpp/blob/master/docs/build.md)

[Vulkan Driver for Termux (Qualcomm devices)](https://www.reddit.com/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)

[DeepSeek-R1-Distill-Qwen-1.5B-GGUF Model](https://huggingface.co/bartowski/DeepSeek-R1-Distill-Qwen-1.5B-GGUF)



---

# ⚖️ License

MIT License

> This toolbox is for personal use and experimentation. Feel free to adapt scripts for your workflow, but credit JADIS if shared publicly.



> "Tools are only as good as the hands that wield them. Build, track, and backup with care."




---

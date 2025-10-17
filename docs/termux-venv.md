# How to instal Virtual Environment in Termux

---

# 🧭 1. Make sure Python is installed

```bash
pkg install python
```

# If you already have it, update just to be safe:

``bash
pkg upgrade python
```

---

# ⚙️ 2. Navigate to your project folder

You can put your venv anywhere, but it’s cleanest to keep it inside your project:

```bash
cd ~/blux-guard    # or any project folder you want
```

---

# 🧪 3. Create a virtual environment

```bash
python -m venv .venv
```
That command creates a folder named .venv containing its own Python and pip installation, isolated from Termux’s global Python.

If you get an error about “ensurepip,” fix it with:

```bash
pkg install python-pip
```
and rerun the venv creation command.


---

# 🔥 4. Activate the environment

Run:

```bash
source .venv/bin/activate
```

You should see your prompt change — something like:

```bash
(.venv) ~/blux-guard $
```

That prefix means your environment is active, and any pip install commands will stay inside .venv.


---

# 🌱 5. (Optional) Deactivate when done

Just type:

```deactivate```

That returns you to Termux’s normal environment.


---

# 🧰 6. (Optional) Add convenience alias

To quickly re-enter your venv:

```bash
echo 'alias venv="source ~/blux-guard/.venv/bin/activate"' >> ~/.bashrc
source ~/.bashrc
```

Now you can type just:

```bash
venv
```

to activate it from anywhere.


---

# 🩵 Quick sanity test

While inside the venv:

```python
python -m pip install requests
python -c "import requests; print('Venv OK ✅')"
```

If that works, your isolated environment is alive.


---
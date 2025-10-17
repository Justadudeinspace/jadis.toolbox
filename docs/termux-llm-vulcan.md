# Termux-LLM-Vulcan


## 1. Termux Deps Install & Setup

```bash
termux-setup-storage
pkg update && pkg install tur-repo x11-repo vulkan-tools shaderc
```

- Vulkan toolchain and required libraries.

---

## 2. Vulkan Driver Install

For GPU acceleration install the Vulkan driver. Download link:

[Vulkan Driver](https://github.com/Jie-Qiao/Android-Termux-LLM-Tutorial/raw/refs/heads/main/mesa-vulkan-icd-wrapper-dbg_24.2.5-5_aarch64.deb)

Move the `vulcan.dep` to Termux root `$HOME` with File Explorer, then install:

```bash
dpkg -i ./mesa-vulkan-icd-wrapper-dbg_24.2.5-7_aarch64.deb
```

Verify Vulkan:

```bash
pkg install vkmark
vulkaninfo
```

`vulkaninfo` should output GPU info if success.

---

## 3. Build `llama.cpp`

Install tools:

```bash
pkg install git cmake
```

Clone needed repos:

```bash
git clone https://github.com/KhronosGroup/Vulkan-Headers.git
git clone https://github.com/ggerganov/llama.cpp.git
```

Begin build:

```bash
cd ~/llama.cpp
cmake -B build -DGGML_VULKAN=ON -DVulkan_LIBRARY=/system/lib64/libvulkan.so -DVulkan_INCLUDE_DIR=~/Vulkan-Headers/include
cmake --build build --config Release
```

**Note**: `DVulkan_LIBRARY` points `libvulkan.so`. Check device support.

---

## 4. Download Model & Activate

Download GGUF from Hugging Face:

[DeepSeek-R1-Distill-Qwen-1.5B-GGUF](https://huggingface.co/bartowski/DeepSeek-R1-Distill-Qwen-1.5B-GGUF)

Download model (e.g., [DeepSeek-R1-Distill-Qwen-1.5B-Q4_K_M.gguf](https://huggingface.co/bartowski/DeepSeek-R1-Distill-Qwen-1.5B-GGUF/blob/main/DeepSeek-R1-Distill-Qwen-1.5B-Q4_K_M.gguf), place in `models` dir of `llama.cpp`.

Locate `llama-cli` in compiled files and run:

```bash
./llama-cli -m /path/to/models/DeepSeek-R1-Distill-Qwen-1.5B-Q4_K_M.gguf -ngl 33
```

**Parameter Explanation**:
- `-ngl 33`: Loads 33 layers of model onto GPU. If VRAM limited, can reduce.
- If want to call model remotely, can use `llama-server` and set `--host 0.0.0.0`.

---0.0.0`.

---/ and set `--host 0.0.0.0`.

---
### 6. References

[llama.cpp/docs/build.md at master · ggerganov/llama.cpp](https://github.com/ggerganov/llama.cpp/blob/master/docs/build.md)

[Qualcomm drivers it's here! : r/termux](https://www.reddit.com/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)alcomm_drivers_its_here/)ts_here/)r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)/)/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)hub.com/ggerganov/llama.cpp/blob/master/docs/build.md)

[Qualcomm drivers it's here! : r/termux](https://www.reddit.com/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)/))](https://www.reddit.com/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)ivers_its_here/)com/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/))nf7s/qualcomm_drivers_its_here/))ost 0.0.0.0`.

---
### 6. References

[llama.cpp/docs/build.md at master · ggerganov/llama.cpp](https://github.com/ggerganov/llama.cpp/blob/master/docs/build.md)

[Qualcomm drivers it's here! : r/termux](https://www.reddit.com/r/termux/comments/1gmnf7s/qualcomm_drivers_its_here/)its_here/)
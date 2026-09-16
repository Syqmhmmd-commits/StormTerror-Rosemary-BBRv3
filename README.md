<div align="center">

# ⚡ StormTerror Kernel

### Custom Kernel for Redmi Note 10S (rosemary)

[![Kernel](https://img.shields.io/badge/Kernel-4.19.325-blue?style=for-the-badge)](https://www.kernel.org/)
[![BBRv3](https://img.shields.io/badge/TCP-BBRv3-orange?style=for-the-badge)](https://github.com/google/bbr)
[![Clang](https://img.shields.io/badge/Clang-24-purple?style=for-the-badge)](https://clang.llvm.org/)
[![Android](https://img.shields.io/badge/Android-15--16-green?style=for-the-badge)](https://www.android.com/)

**Performance-focused kernel with BBRv3 network optimization**

[Download](#-download) • [Features](#-features) • [Installation](#-installation) • [Source](#-source-code) • [Credits](#-credits)

</div>

---

## 📱 Supported Devices

| Device | Codename | Status |
|--------|----------|--------|
| Redmi Note 10S | `rosemary` | ✅ |
| Redmi Note 10S NFC | `rosemary` | ✅ |
| Redmi Note 10S (India) | `maltose` | ✅ |
| POCO M5s | `secret` | ✅ |

## ✨ Features

### 🌐 Network
- **BBRv3 TCP Congestion Control** — backported from latest upstream
  - Higher throughput, lower latency
  - Better packet loss handling
  - Optimized for mobile networks

### ⚙️ Core
- **Kernel 4.19.325** — latest stable 4.19.y with CIP + ST patches
- **Neutron Clang 24** — modern toolchain for better optimization
- **Full LTO-friendly** — built with LLVM_IAS=1

### 🔧 Compatibility
- Android 12 — 16
- LineageOS 23.2 (Android 16)
- AnyKernel3 — works with any ROM
- Magisk / KernelSU friendly

## 🚀 Installation

### Via TWRP Recovery

1. **Boot into TWRP Recovery**

2. **⚠️ Backup Boot Partition** (MANDATORY)
- TWRP → Backup → Select **Boot** → Swipe to backup
- This is your safety net if something goes wrong

3. **Flash the kernel**
- TWRP → Install → Select `StormTerror-Rosemary-BBRv3.zip` → Swipe to confirm

4. **Reboot System**

### Via Kernel Flasher (Root)

If you have root access, you can use apps like:
- **Franco Kernel Manager**
- **EX Kernel Manager**
- **Kernel Flasher**

## ✅ Verification

After flashing, verify with Termux or ADB:

```bash
# Check kernel version
uname -r
# Expected: 4.19.325-StromTerror-perf+

# Check active TCP congestion control
cat /proc/sys/net/ipv4/tcp_congestion_control
# Expected: bbr

# Verify BBRv3 is loaded
ss -tio | grep bbr
# Expected: bbr:(bw:..., pacing_gain:2.77344, cwnd_gain:2)

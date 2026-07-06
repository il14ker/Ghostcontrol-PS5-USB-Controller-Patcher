# PS5 payload SDK (local install)

This machine uses the binary release from [ps5-payload-dev/sdk](https://github.com/ps5-payload-dev/sdk).

```bash
export PS5_PAYLOAD_SDK=/home/deck/ps5-payload-sdk-install/ps5-payload-sdk
```

**Build (Arch toolchain via distrobox):** host SteamOS does not ship `clang`/`make` on the read-only root; use the `gc-build` container:

```bash
distrobox enter gc-build -- bash -lc '
  export PS5_PAYLOAD_SDK=/home/deck/ps5-payload-sdk-install/ps5-payload-sdk
  cd /home/deck/Documents/GitHub/Ghostcontrol-PS5-USB-Controller-Patcher/payload
  make clean all PS5_PAYLOAD_SDK="$PS5_PAYLOAD_SDK"
'
```

Requires `llvm` in the container so `prospero-llvm-config` resolves host `clang` (target `x86_64-sie-ps5`).
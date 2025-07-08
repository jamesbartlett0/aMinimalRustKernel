# Rust Kernel

A freestanding binary kernel implementation written in Rust.

## Prerequisites

- Rust toolchain (stable or nightly)
- QEMU system emulator

## Setup & Installation

### 1. Install bootimage

The `bootimage` tool is required to create bootable disk images from Rust kernel binaries.

```bash
cargo install bootimage
```

### 2. Add LLVM tools component

Add the LLVM tools preview component to your Rust toolchain:

```bash
rustup component add llvm-tools-preview
```

### 3. Install QEMU

Download and install QEMU from the official website: https://www.qemu.org/

**Note:** The `qemu-system` component is required for running the kernel.

## Building & Running

### Create bootable disk image

Build the kernel and create a bootable disk image:

```bash
cargo bootimage
```

This command will:
- Compile the kernel binary
- Create a bootable disk image in the `target/` directory

### Boot in QEMU

Run the kernel in the QEMU emulator:

```bash
qemu-system-x86_64 -drive format=raw,file=target/x86_64_os/debug/bootimage-aFreestandingBinary.bin
```

## Project Structure

- `/src` - Kernel source code
- `/target` - Build artifacts and bootable images
- `Cargo.toml` - Project configuration and dependencies

## Development

This kernel is built as a freestanding binary, meaning it doesn't rely on the standard library and runs directly on bare metal.
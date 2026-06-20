# aeroport-core

This repository contains the primary macOS host application for the AeroPort ecosystem. It is responsible for hypervisor lifecycle management, communication protocols over virtual sockets, and compositing guest windows natively into macOS.

## Prerequisites

* Apple Silicon Mac (M1, M2, M3, M4 family)
* macOS 14.0 Sonoma or later
* Xcode 15.0 or later
* Swift 5.9+

## Core Subsystems

* **Hypervisor Engine**: Wraps Apple's `Virtualization.framework` to configure and boot the Windows 11 ARM64 guest environment, assigning hardware allocations, storage attachments, and VirtIO file system shares.
* **VSOCK Listener**: Implements a lightweight, asynchronous multiplexing protocol over VirtIO sockets to coordinate window lifecycle, mouse/keyboard input events, and clipboard data with the guest agent.
* **Surface Compositor**: Captures raw shared memory frame pointers provided by the guest and renders them efficiently into transparent native AppKit panels using Metal-backed layers.
* **Storefront Dashboard**: A native SwiftUI interface that parses a remote verified application JSON registry, allowing users to initiate streamlined installation routines.

## Building from Source

1. Clone the repository:
   ```bash
   git clone [https://github.com/AeroPortOSS/aeroport-core.git](https://github.com/AeroPortOSS/aeroport-core.git)
   cd aeroport-core

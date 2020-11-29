[![](https://camo.githubusercontent.com/e2ad169be7fbb53a876ab41ae4a20d5b8586955bde78ccb002f63feb700982c1/68747470733a2f2f692e696d6775722e636f6d2f4c47363345714b2e706e67)](https://camo.githubusercontent.com/e2ad169be7fbb53a876ab41ae4a20d5b8586955bde78ccb002f63feb700982c1/68747470733a2f2f692e696d6775722e636f6d2f4c47363345714b2e706e67)

[
[![Build Status](https://camo.githubusercontent.com/a9b20ee503383b46bf579942dd82d4eb52f2dabedfae57d9661860de9d80f443/68747470733a2f2f7472617669732d63692e6f72672f506f432d436f6e736f727469756d2f73636176656e6765722e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/PoC-Consortium/scavenger)  [![License: GPL v3](https://camo.githubusercontent.com/400c4e52df43f6a0ab8a89b74b1a78d1a64da56a7848b9110c9d2991bb7c3105/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4c6963656e73652d47504c76332d626c75652e737667)](https://www.gnu.org/licenses/gpl-3.0)

# [](https://github.com/PoC-Scavenger/scavenger#scavenger---poc-miner-in-rust)Scavenger - PoC miner in Rust

### [](https://github.com/PoC-Scavenger/scavenger#features)Features

-   windows, linux, macOS, android & more
-   x86 32 & 64bit, arm, aarch64
-   direct io
-   avx512f, avx2, avx, sse, neon
-   opencl
-   fastest PoC miner there is

### [](https://github.com/PoC-Scavenger/scavenger#documentationwiki)Documentation/Wiki

[https://github.com/PoC-Consortium/scavenger/wiki](https://github.com/PoC-Scavenger/scavenger/wiki)

### [](https://github.com/PoC-Scavenger/scavenger#binary--source-code-releases)Binary + source code releases

[https://github.com/PoC-Consortium/scavenger/releases](https://github.com/PoC-Scavenger/scavenger/releases)

Scavenger can also be installed directly via cargo:

cargo install scavenger

### [](https://github.com/PoC-Scavenger/scavenger#development-requirements)Development Requirements

-   new version of rust, stable toolchain

### [](https://github.com/PoC-Scavenger/scavenger#compile-test-)Compile, test, ...

Binaries are in  **target/debug**  or  **target/release**  depending on optimization.

# decide on features to run/build:
simd: support for SSE2, AVX, AVX2 and AVX512F (x86_cpu)
neon: support for Arm NEON (arm_cpu)
opencl: support for OpenCL (gpu)

# build debug und run directly
e.g. cargo run --features=simd    #for a cpu version with SIMD support

# build debug (unoptimized)
e.g cargo build --features=neon   #for a arm cpu version with NEON support

# build release (optimized)
e.g. cargo build --release --features=opencl,simd    #for a cpu/gpu version

# test
cargo test  [--features={opencl,simd,neon}]

### [](https://github.com/PoC-Scavenger/scavenger#run)Run

scavenger --help

### [](https://github.com/PoC-Scavenger/scavenger#config)Config

The miner needs a  **config.yaml**  file with the following structure:

[https://github.com/PoC-Scavenger/scavenger/blob/master/config.yaml](https://github.com/PoC-Scavenger/scavenger/blob/master/config.yaml)

### [](https://github.com/PoC-Scavenger/scavenger#docker)Docker

A docker image based on alpine linux is built automatically on every commit to master:  `pocconsortium/scavenger`  This image will use only your cpu.

To run it on the fly use something like this:

```
docker run \
--rm \
--name scavenger \
--volume /path/to/your/config.yaml:/data/config.yaml \
--volume /path/to/your/disks:/disks \
pocconsortium/scavenger

```

Alternatively a docker compose file could look like this:

```
version: '2'
services:
  scavenger:
    image: pocconsortium/scavenger
    restart: always
    volumes:
      - /path/to/your/disks:/disks
      - /path/to/your/config.yaml:/data/config.yaml

```

### [](https://github.com/PoC-Scavenger/scavenger#donate)Donate

-   bold: BURST-8V9Y-58B4-RVWP-8HQAV
    -   architecture
    -   linux support
-   JohnnyDeluxe: BURST-S338-R6VC-LTFA-2GC6G
    -   open cl
    -   direct io
    -   shabal optimizations
    -   windows support

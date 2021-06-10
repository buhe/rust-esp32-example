# Rust on Xtensa Installation for macOS arm64

Tested OS: macOS Big Sur arm64

## Commands

```
mkdir -p ~/.rustup/toolchains/xtensa

wget https://dl.espressif.com/dl/idf-rust/dist/aarch64-apple-darwin/rust-1.50.0-dev-aarch64-apple-darwin.tar.xz
tar xvf rust-1.50.0-dev-aarch64-apple-darwin.tar.xz
pushd rust-1.50.0-dev-aarch64-apple-darwin
./install.sh --destdir=~/.rustup/toolchains/xtensa --prefix="" --without=rust-docs
popd

wget https://dl.espressif.com/dl/idf-rust/dist/aarch64-apple-darwin/rust-src-1.50.0-dev.tar.xz
tar xvf rust-src-1.50.0-dev.tar.xz
pushd rust-src-1.50.0-dev
./install.sh --destdir=~/.rustup/toolchains/xtensa --prefix=""
popd

rustup default xtensa

wget https://dl.espressif.com/dl/idf-rust/dist/aarch64-apple-darwin/xtensa-esp32-elf-llvm11_0_0-aarch64-apple-darwin.tar.xz
tar xf xtensa-esp32-elf-llvm11_0_0-aarch64-apple-darwin.tar.xz
export PATH="`pwd`/llvm-patch/bin/:$PATH"

wget https://github.com/espressif/rust-esp32-example/archive/refs/heads/main.zip
unzip main.zip
cd rust-esp32-example-main/rustlib
cargo build --release
cd ..
idf.py build
```

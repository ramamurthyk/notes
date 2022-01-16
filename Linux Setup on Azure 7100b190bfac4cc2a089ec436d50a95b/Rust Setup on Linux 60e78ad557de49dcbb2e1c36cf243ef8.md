# Rust Setup on Linux

Install Rust from [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)

```bash
curl --proto '=https' --tlsv1.2 -sSf [https://sh.rustup.rs](https://sh.rustup.rs/) | sh
```

Create an app and verify.

```bash
cargo new rust_app
cargo run
```

If there is an error such as error: linker `cc` not found, it needs additional tools installed.

Install

```bash
sudo apt install build-essential
```

Now re-run the verification step.

VS code setup.

Install Rust extension.

[Rust - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust)

Install CodeLLDB extension for debugging.

[CodeLLDB - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vadimcn.vscode-lldb)
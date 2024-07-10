##Setting environment

```
apt update
apt install git
apt install curl
apt install gcc
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs/ | sh
rustup install nightly
. "$HOME/.cargo/env"
rustup default nightly
```

##Clone git repo

```
cd home
git clone https://github.com/Lind-Project/safeposix-rust.git
```

##Build

```
cargo build
```

# mct
menstrual cycle tracker built in POSIX shell

## installation
### quick install (single user)
```sh
# download the script
curl -o ~/.local/bin/mct https://raw.githubusercontent.com/oatbiscuit/mct/main/mct
chmod +x ~/.local/bin/mct

# Make sure ~/.local/bin is in your PATH
# Add this to your ~/.bashrc or ~/.zshrc if not already:
export PATH="$HOME/.local/bin:$PATH"
```

### system-wide install
```
# Install to /usr/local/bin (requires sudo)
sudo curl -o /usr/local/bin/mct https://raw.githubusercontent.com/oatbiscuit/mct/main/mct
sudo chmod +x /usr/local/bin/mct
```

### manual install
```sh
# Clone the repository or download the script
git clone https://github.com/oatbiscuit/mct.git
cd mct

# Make executable and copy to your PATH
chmod +x mct
cp mct ~/.local/bin/  # or /usr/local/bin/
```

### verify installation
```sh
mct --version
# should output: mct <version>
```

### uninstallation
```sh
# Remove the script
rm ~/.local/bin/mct   # or /usr/local/bin/mct

# Optional: Remove data file
rm -rf ~/.local/share/mct/
```

## help
```sh
~ $ mct -h
Usage: mct [OPTION] [COMMAND] [DATE]

DATE format: YYYY-MM-DD (e.g., 2026-09-01)

Commands:
    r, record   [DATE]      Record a cycle day (default: today)
    d, delete   [DATE]      Delete a cycle day (default: today)
    p, predict              Predict next start date.
    s, stats                Show current stats.

Options:
    -h, --help              Show this help message.
    -v, --version           Show version information
```

## dependencies
- awk
- grep
- sort
- date
- mktemp

> [!NOTE]
> These utilities are standard on most Unix-like systems (Linux, macOS, BSD) and are typically installed by default.

## examples
```sh
# Record today
mct r

# Record a specific date
mct r 2026-09-01

# View statistics
mct s

# Predict next cycle
mct p

# Delete a record
mct d 2026-09-01
```

## how to use
To use `mct`, simply run `mct r` to record your first day, this will create a file called `cycles` in `~/.local/share/mct/` folder.

You can also supply a custom date with `mct r YYYY-MM-DD`

The output of the file is just a list of dates that will look like this:

```sh
~ $ cat ~/.local/share/mct/cycles 
2025-02-28
2025-02-29
2025-03-01
2025-03-02
2025-03-03
2025-03-25
2025-03-26
2025-03-27
2025-03-28
...
```

> [!NOTE]
> The `cycles` file will be `chmod 600`, and the `~/.local/share/mct/` folder is `chmod 700` for added privacy.

**Permissions:**
- `~/.local/share/mct/` -> `700` (only you can read/write/execute)
- `~/.local/share/mct/cycles` -> `600` (only you can read/write)

## TODO
- [x] Add large gap anomaly checker (for pregnancies or illness) 
- [ ] Add git support
- [ ] Add optional gpg encryption support
- [x] Add colour output

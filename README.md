# mct
menstrual cycle tracker built in POSIX shell

## help
```sh
~ $ mct -h
Usage: mct [OPTION] [COMMAND] [DATE]

Commands:
    r, record   [DATE]      Record a cycle day (default: today)
    d, delete   [DATE]      Delete a cycle day (default: today)
    p, predict              Predict next start date.
    s, stats                Show current stats.

Options:
    -h, --help              Show this help message.
    -v, --version           Show version information
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

You can view your stats with `mct s`:

```sh
~ $ mct s
total days recorded: 43
total cycles: 9
first recorded: 2025-02-28
last recorded: 2025-09-08
average cycle length: 4 days
average days between cycles: 21 days
cycle range: 20-22 days
```

and predict your next cycle with `mct p`:

```sh
~ $ mct p
last cycle: 2025-09-04 to 2025-09-08 (5 days)
average cycle length: 21 days (based on 7 cycles)
average period duration: 4 days

predicted next cycle:
  start: 2025-09-30
  end:   2025-10-03
  duration: 4 days
```

## TODO
- [] Add large gap anomaly checker (for pregnancies or illness) 
- [] Add git support
- [] Add optional gpg encryption support
- [] Add colour output
- [] Symptom tracking?

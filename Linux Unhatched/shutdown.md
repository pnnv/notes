The `shutdown` command arranges for the system to be brought down in a safe way. All logged in users are notified that the system is going down and within the last five minutes leading up to the shutdown, new logins are prevented.

```bash
sudo shudown [OPTIONS] TIME [MESSAGE]
```

```bash
sudo shutdown now
```

Unlike other commands used to bring the system down, the `shutdown` command requires a time argument specifying when the shutdown should begin. Formats of this time argument can be the word `now`, a time of day in the format `hh:mm` or the number of minutes to delay in the format `+minutes`.

The `shutdown` command also has an optional message argument, indicating a message that will appear in the terminals of all users. For example:

```bash
sudo shutdown +1 "Goodbye World!"
```

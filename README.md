# AutoenvFish

Directory-based environments for fish, inspired by Kenneth Reitz's [autoenv]. If you miss that from your bash-using days, then miss it no longer.

## What is it?

If a directory (or one of its parents) contains a `.env.fish` file, it will be sourced when you `cd` into it.

In practice, you could do whatever you like—the `.env.fish` file is sourced and run like any fish script. In practice, I end up using it mainly for setting project-specific environment variables for local development:

```fish
set -gx DJANGO_SECRET_KEY "s00persekr1t"
set -gx DJANGO_SETTINGS_MODULE "myappname.settings.local"
set -gx AWS_ACCESS_KEY_ID "xxxxxxxxxxxxxxxxxxxx"
set -gx AWS_SECRET_ACCESS_KEY "yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy"
```

See some more stuff about security implications below.

## installation

1. Put `autoenv.fish` somewhere handy. I like to put it in `~/.config/fish/autoenv.fish`.
2. Source the file in your `config.fish`:
```fish
# load autoenv.fish
. ~/.config/fish/autoenv.fish
```
3. If you want it to take effect for your current terminal sessions, reload your config.fish by typing `. path/to/your/config.fish` in every terminal window. If you're using [iTerm2], typing `⌘⇧I` is handy for broadcasting what you type to every open terminal.


## Ssage

Create a `.env.fish` file somewhere. Fill it up with whatever valid fish script you like. It'll get sourced whenever you are in the directory, and you'll see a message telling you so.


## Security Considerations

AutoenvFish won't bat an eyelash if your `.env.fish` includes a line like `sudo rm -rf /*`. Be careful what you put in your files.

One of the things which [autoenv] does nicely is hashing of the executed files and a warning every time it changes. I'd like to add that in a future release.


[autoenv]: https://github.com/kennethreitz/autoenv
[iterm2]: http://www.iterm2.com
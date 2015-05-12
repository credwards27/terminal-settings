# Terminal Settings

Bash and terminal environment settings.

## Usage

The root of this repo represents your home directory, and all files should be linked/copied to their corresponding locations.

To use the custom bash configurations, include the following code at the top of `.bash_profile`:

```bash
if [ -f ~/.bash_common_profile ]; then
    . ~/.bash_common_profile
fi
```

The above snippet will load the custom configurations into bash.

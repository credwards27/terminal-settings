# Terminal Settings

Bash and terminal environment settings.

## Usage

The root of this repo represents your home directory, and all files (excluding
repo files) should be linked/copied to their corresponding locations.

To use the custom bash configurations, include the following code at the top of
`.bash_profile`:

```bash
if [ -f ~/.bash_common_profile ]; then
    . ~/.bash_common_profile
fi
```

The above snippet will load the custom configurations into bash.

### Executables

A `bin/` directory is included with common shared executables. As system
configurations can vary greatly, these are not sourced by default in
`.bash_common_profile`. Instead, they should be linked or sourced as necessary
depending on each system configuration's needs.

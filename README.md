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

### Git Configurations

**Note:** By default, git configurations are not synced automatically;
`git-config` must be run manually.

Global git configurations can be shared using the `bin/git-config` and
`.git_common_sync` files. The `.git_common_sync` file contains shared
configuration settings, and should be symlinked in the user's home directory as
described above. A local `.git_sync` may also be placed in the user's home
directory for settings that should not be shared, and setting values that
override those in `.git_common_sync`.

When `git-config` is run, `.git_common_sync` is sourced, followed by
`.git_sync`. **Note:** Settings defined in either of the sync files will
overwrite any settings made directly from the command line. Settings not present
in either of the sync files will remain unchanged.

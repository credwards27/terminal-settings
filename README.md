# Terminal Settings

Bash and terminal environment settings.

## Installation

Run the `home/bin/terminal-sync-setup` script to automatically configure the
user's environment for shared settings. By default, binaries will not be linked.

**Note:** The setup script will never overwrite existing files, and should warn
if a conflict occurs.

Alternatively, the terminal settings can be set up manually as described below.

The `home/` directory of this repo represents your home directory, and all files
and directories in it should be symlinked/copied to the user's actual home
directory. The file and directory names in the user's home directory should
match those in this `home/` directory.

### Options

- `[-b|--bin <path>]`
	- Symlinks the shared executables in the directory specified by `<path>`.
		The symlinked will be named `common`, as in `<path>/common`. This must
		be added to `$PATH` manually.

- `[-s|--snippet]`
	- This flag will create a sample `.bash_profile_setup_snippet` file in the
		user's home directory, which will contain the `.bash_profile` snippet
		needed to include the shared settings. This snippet should be added
		manually to the top of the user's `.bash_profile`.
	- The `.bash_profile_setup_snippet` file created by this flag can be safely
		removed after it has been copied into `.bash_profile`.

## Usage

Running the setup script with the `[-s|--snippet]` flag will create a sample
`.bash_profile_setup_snippet` file in the user's home directory containing the
following snippet. This code block can then be copied manually into the user's
`.bash_profile` at the top of the file:

```bash
if [ -f ~/.bash_common_profile ]; then
    . ~/.bash_common_profile
fi
```

After running the setup script or manually linking the settings files from the
repo, source `.bash_profile` for the changes to take effect.

### Executables

A `home/bin/` directory is included with common shared executables. As system
configurations can vary greatly, these are not sourced by default in
`.bash_common_profile`. Instead, they should be linked or sourced as necessary
depending on each system configuration's needs. See installation instructions
for how to optionally do this with the setup script.

### Git Configurations

**Note:** By default, git configurations are not synced automatically;
`git-config` must be run manually.

Global git configurations can be shared using the `home/bin/git-config` and
`.git_common_sync` files. The `.git_common_sync` file contains shared
configuration settings, and should be symlinked in the user's home directory as
described above. A local `.git_sync` may also be placed in the user's home
directory for settings that should not be shared, and setting values that
override those in `.git_common_sync`.

When `git-config` is run, `.git_common_sync` is sourced, followed by
`.git_sync`. **Note:** Settings defined in either of the sync files will
overwrite any settings made directly from the command line. Settings not present
in either of the sync files will remain unchanged.

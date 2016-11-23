### Installing packages

#### Installing specific packages
To install a single package or list of packages (including dependencies), issue the following command:
`# pacman -S package_name1 package_name2 ...`

To install a list of packages with regex
`# pacman -S $(pacman -Ssq package_regex)`

Sometimes there are multiple versions of a package in different repositories, e.g. extra and testing. To install the former version, the repository needs to be defined in front:
`# pacman -S extra/package_name`

To install a number of packages sharing similar patterns in their names -- not the entire group nor all matching packages; eg. plasma:
`# pacman -S plasma-{desktop,mediacenter,nm}`

Of course, that is not limited and can be expanded to however many levels needed:
`# pacman -S plasma-{workspace{,-wallpapers},pa}`

#### Installing package groups
Some packages belong to a group of packages that can all be installed simultaneously. For example, issuing the command:
`# pacman -S gnome`

will prompt you to select the packages from the gnome group that you wish to install.
Sometimes a package group will contain a large amount of packages, and there may be only a few that you do or do not want to install. Instead of having to enter all the numbers except the ones you do not want, it is sometimes more convenient to select or exclude packages or ranges of packages with the following syntax:
`Enter a selection (default=all): 1-10 15`
which will select packages 1 through 10 and 15 for installation, or:
`Enter a selection (default=all): ^5-8 ^2`
which will select all packages except 5 through 8 and 2 for installation.
To see what packages belong to the gnome group, run:
`# pacman -Sg gnome`

### Removing packages

To remove a single package, leaving all of its dependencies installed:
`# pacman -R package_name`

To remove a package and its dependencies which are not required by any other installed package:
`# pacman -Rs package_name`

To remove a package, its dependencies and all the packages that depend on the target package:
**Warning: This operation is recursive, and must be used with care since it can remove many potentially needed packages.**
`# pacman -Rsc package_name`

To remove a package, which is required by another package, without removing the dependent package:
`# pacman -Rdd package_name`

pacman saves important configuration files when removing certain applications and names them with the extension: .pacsave. To prevent the creation of these backup files use the `-n` option:
`# pacman -Rn package_name`
**Note: pacman will not remove configurations that the application itself creates (for example "dotfiles" in the home folder).**

### Upgrading packages

pacman can update all packages on the system with just one command. This could take quite a while depending on how up-to-date the system is. This command can synchronize the repository databases and update the system's packages (excluding "local" packages that are not in the configured repositories):
`# pacman -Syu`

>**Tip:**
>- Remember that *pacman*'s output is logged in `/var/log/pacman.log`.
>- You can use a log viewer such as `wat-git`(AUR) to search the pacman logs.

### Querying package databasesQuerying package databases

pacman queries the local package database with the `-Q` flag; see:
`$ pacman -Q --help`

and queries the sync databases with the `-S` flag; see:
`$ pacman -S --help`

pacman can search for packages in the database, searching both in packages' names and descriptions:
`$ pacman -Ss string1 string2 ...`

Sometimes, `-s`'s builtin ERE can cause a lot of unwanted results, so it has to be limited to match the package name only; not the description nor any other field:
`# pacman -Ss '^vim-'`

To search for already installed packages:
`$ pacman -Qs string1 string2 ...`

To display extensive information about a given package:
`$ pacman -Si package_name`

For locally installed packages:
`$ pacman -Qi package_name`

Passing two `-i` flags will also display the list of backup files and their modification states:
`$ pacman -Qii package_name`

To retrieve a list of the files installed by a package:
`$ pacman -Ql package_name`

To verify the presence of the files installed by a package:
`$ pacman -Qk package_name`

Passing the `k` flag twice will perform a more thorough check.
One can also query the database to know which package a file in the file system belongs to:
`$ pacman -Qo /path/to/file_name`

To list all packages no longer required as dependencies (orphans):
`$ pacman -Qdt`

To list all packages explicitly installed and not required as dependencies:
`$ pacman -Qet`

To list a dependency tree of a package:
`$ pactree package_name`

# GitHub workflow for setting up Qt6 using vcpkg (on Windows)
This repository was created for evaluating using _vcpkg_ for installing the _Qt6_ packages (for development).
In general, this is necessary for building applications that depend on the _Qt_ (development) packages.

The workflow configures a GithHub _actions:cache_ so that the binaries are only build (from source) the 1st time the workflow is executed.\
The cache was setup so that it must be manually invalidated (e.g. deleted) for trigerrring the rebuilding of the packages.\
This is done to avoid unwanted (long) recompilations of the respective sources.

On the initial test:
- The 1st execution of the workflow, installing the _qtbase_ and _qtbase[windeployqt]_ packages, took __1h30m__ (both the debug and release variants were built).
- The subsequent executions took about __1 minute__ for installing the same packages (which got installed from the cached binaries).

The size of total cached data was about __2.3GB__ (before compression). The resulting cache size was about __1GB__.

The following folders were cached:
- 569M	/vcpkg/bincache
- 1.7G	/vcpkg/downloads

Note that vcpkg requires the contents of the downloads folder for installing the matched previouly compiled binaries in the bincache.

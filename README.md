# IoPathUtils
Path and library directory utilities for the Io language

## Setting Up ##

Simply place LibPath.io and PathUtil.io in a search path.  It's often easiest to simply place them in the root of your package or project.

## API ##

### PathUtil ###

PathUtil is a small collection of utilities for handling paths within your package or project

**getDirectoryPaths**

This will return the names of all items found within a provided directory.  Directories named '.' and '..' will be omitted.

```io
PathUtil getDirectoryPaths("path/to/somewhere")
// returns list("path", "names", "here")
```

**getSearchPathByDirName**

This will return the first path in the search paths which contains the provided directory name.

```io
PathUtil getSearchPathByDirName("myPackage")
// returns "/path/to/myPackage"
```

### LibPath ###

LibPath is a proto for setting up and loading library directories within your package or project.  Though not intended for use by itself, this can be used as a rudimentary package setup tool.

```io
libPathInstance := LibPath clone
```

**setLaunchPath**

Set the launch path if different than the default -- System launchPath:

```io
libPathInstance setLaunchPath("/my/preferred/launch/path")
```

**setLibPathName**

Set the path name for your libraries directory if different than the default -- "libs":

```io
libPathInstance setLibPathName("someLibraries")
```

**addPath**

Add a search path directly to the Importer search paths:

```io
libPathInstance addPath("/my/search/path")
```

**addPathWithBase**

Add a search path to Importer search paths with separate base path and path name:

```io
libPathInstance addPathWithBase("/my/base/path", "pathName")
```

**addPathWithBaseByDirName**

Add a search path to Importer search paths with a base path as it is found by directory name:

```io
libPathInstance addPathWithBaseByDirName("myProject", "pathName")
```

**addLibPaths**

Add all library paths to Importer search paths based on defined launch path and library path name

```io
libPathInstance addLibPaths()
```
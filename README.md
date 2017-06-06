# Bumpy

Bumpy is a tool to maintain version information across multiple files found in the current working directory using a configuration file which consists of glob patterns and regular expressions.

## Usage

Bumpy is a command line tool:

```
bumpy <command> <arguments>
```

### List

```
bumpy -l
```

Lists all versions.

**Example:** `bumpy -l`

```
\Source\Bumpy\Properties\AssemblyInfo.cs (35): 0.1.0.0
\Source\Bumpy\Properties\AssemblyInfo.cs (36): 0.1.0.0
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (34): 0.1.0.0
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (35): 0.1.0.0
\NuSpec\Chocolatey\Bumpy.nuspec (5): 0.1.0
```

### Create Configuration

```
bumpy -c
```

Creates an empty `.bumpyconfig` file.

### Increment

```
bumpy -i <one-based index number>
```

Increments the specified component of each version.

**Example:** `bumpy -i 2`

```
\Source\Bumpy\Properties\AssemblyInfo.cs (35): 0.1.0.0 -> 0.2.0.0
\Source\Bumpy\Properties\AssemblyInfo.cs (36): 0.1.0.0 -> 0.2.0.0
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (34): 0.1.0.0 -> 0.2.0.0
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (35): 0.1.0.0 -> 0.2.0.0
\NuSpec\Chocolatey\Bumpy.nuspec (5): 0.1.0 -> 0.2.0
```

### Write

```
bumpy -w <version string>
```

Overwrites a version with another version.

This command could be used to e.g:

- Unify the version information of projects and files in a solution
- Change the version information of a newly created project to be in line with other projects in a solution

**Example:** `bumpy -w 1.2.0.5`

```
\Source\Bumpy\Properties\AssemblyInfo.cs (35): 0.2.0.0 -> 1.2.0.5
\Source\Bumpy\Properties\AssemblyInfo.cs (36): 0.2.0.0 -> 1.2.0.5
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (34): 0.2.0.0 -> 1.2.0.5
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (35): 0.2.0.0 -> 1.2.0.5
\NuSpec\Chocolatey\Bumpy.nuspec (5): 0.2.0 -> 1.2.0.5
```

### Assign

```
bumpy -a <one-based index number> <version number>
```

Replaces the specified component of a version with a new number. This command could be used by a CI server to inject a build number.

**Example:** `bumpy -a 3 99`

```
\Source\Bumpy\Properties\AssemblyInfo.cs (35): 1.2.0.5 -> 1.2.99.5
\Source\Bumpy\Properties\AssemblyInfo.cs (36): 1.2.0.5 -> 1.2.99.5
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (34): 1.2.0.5 -> 1.2.99.5
\Source\Bumpy.UnitTests\Properties\AssemblyInfo.cs (35): 1.2.0.5 -> 1.2.99.5
\NuSpec\Chocolatey\Bumpy.nuspec (5): 1.2.0.5 -> 1.2.99.5
```

## Configuration

Bumpy's configuration is based on the presence of a `.bumpyconfig` file in the current working directory. This file dictates the behaviour of Bumpy using a pair of glob patterns and regex expressions, e.g:

```
# Searches for a version of the format a.b.c in all .nuspec files in the folder NuSpec
NuSpec\**\*.nuspec = (?<version>\d+\.\d+\.\d+)
```

For each line of a specific file (found through the glob pattern) Bumpy uses the provided regular expression to extract the named regex group `?<version>`. Note that the content of the `?<version>` group matches the form`\d+(\.\d+)*` (meaning `1`, `1.0`, `1.0.0`, `1.0.0.0`, ...) as this is the only format that is currently supported by Bumpy.

## Example

Check out the `.bumpyconfig` file to see how I manage Bumpy's version files using Bumpy.

## Trivia

- The name Bumpy is loosely based on "to bump something up" instead of the original meaning of the word (as in "a bumpy road")
- Inspiration taken from [Zero29](https://github.com/ploeh/ZeroToNine)

## License

[MIT](http://opensource.org/licenses/MIT)

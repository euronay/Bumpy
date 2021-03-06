# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [0.7.0] - 2017-12-23

### Added

- [#23](https://github.com/fwinkelbauer/Bumpy/issues/23) Added support for code pages in `.bumpyconfig`
- [#24](https://github.com/fwinkelbauer/Bumpy/issues/24) Added new command incrementonly. Thank you [@euronay](https://github.com/euronay) for your contribution!

### Fixed

- [#22](https://github.com/fwinkelbauer/Bumpy/issues/22) Fixed a case in which `bumpy write` would perform in an inconsistent manner

## [0.6.0] - 2017-10-18

### Changed

- **Breaking Change:** Redesigned the command line interface to be similar to tools such as git or chocolatey. This change also introduces new options. See the updated `README` file for more information

### Removed

- **Breaking Change:** Removed the command to list profiles. Profiles are now shown when calling `bumpy list`

## [0.5.0] - 2017-09-20

### Removed

- Removed GitReleaseManager from the build script

### Changed

- Adopted keepachangelog.com
- The glob pattern implementation now relies on pure regex instead of relying on external NuGet packages
- The pattern "\*\*\Foo.txt" will:
  - match files named "Foo.txt"
  - not match other files such as "SomeFoo.txt"

## [0.4.1] - 2017-08-24

### Fixed

- The 0.4.0 packages were unlisted because they were missing a library

### Changed

- [#19](https://github.com/fwinkelbauer/Bumpy/issues/19) **Breaking Change** Glob pattern: The re-introduction of glob patterns might break existing `.bumpyconfig` files. Please read the updated documentation!
- [#17](https://github.com/fwinkelbauer/Bumpy/issues/17) Automate Chocolatey verification

## [0.3.0] - 2017-07-17

### Fixed

- [#18](https://github.com/fwinkelbauer/Bumpy/issues/18) Bug when parsing configuration files with the '=' character in a regular expression

### Added

- [#14](https://github.com/fwinkelbauer/Bumpy/issues/14) Automate GitHub releases

## [0.2.1] - 2017-06-28

### Added

- [#10](https://github.com/fwinkelbauer/Bumpy/issues/10) Add missing information to the help command
- [#12](https://github.com/fwinkelbauer/Bumpy/issues/12) Add automation steps to publish packages

## [0.2.0] - 2017-06-27

### Added

- [#12](https://github.com/fwinkelbauer/Bumpy/issues/2) Support other version formats
- [#16](https://github.com/fwinkelbauer/Bumpy/issues/6) Add encoding configuration 

## [0.1.0] - 2017-06-19

### Added

- Initial release

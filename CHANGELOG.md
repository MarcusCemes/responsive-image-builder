# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project
adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [4.0.0] - 2020-06-06

Responsive Image Builder has been split into several packages.
This makes it more modular and reduces the installation size.
The core functionality of IPP has been upgraded to process an image pipeline, instead
of fixed functionality based around breakpoint generation.

- @ipp/broker - Task distribution
- @ipp/cli - UI
- @ipp/common - Shared interfaces
- @ipp/core - Image processing
- @ipp/compress - Image compression
- @ipp/primitive - Primitive SVG generation
- @ipp/testing - Shared testing utilities

## [3.1.3] - 2020-01-13

### Changed

- Updated dependencies

### Fixed

- Width/height preset properties now (correctly) accept numbers
- When merging configs, default presets are now overwritten

## [3.1.1] - 2019-06-06

### Changed

- Update dependencies (fixes security vulnerabilities)

## [3.1.0] - 2019-04-26

### Added

- SVG Tracing with _potrace_
- Better modularization of the pipeline for easier extensibility with newer features

### Fixed

- Image converting (`convert` option would do nothing)
- Small formatting errors, typos

## [3.0.1] - 2019-04-02

### Fixed

- CLI ('bin' folder was not whitelisted for deployment)

## [3.0.0] - 2019.04-02

The third major update that involved a rewrite of the worker thread. The image export system is now
more modular and customizable, making it easier to add "filters" in the future to modify image
streams.

This update introduces BREAKING CHANGES to the manifest file and program errors.

### Added

- Image fingerprinting! Don't rely on names anymore for resolution, but on a checksum of the
  original image!
- Temporary files when exporting, less chance of conflicts and overwriting, with negligible
  performance cost
- Better and safer cleanup in case of failed exports
- Custom file naming using template literals!
- A better code-based error system
- Visual Studio Code debug scripts for node `--inspect` debugging (instead of console logging)
- Typescript interface exports
- Code of Conduct + better contributing guide
- Short file header

### Changed

- Rewrote the worker thread to use functions instead of classes, separated into more files, making
  the worker more modular and upgradable in the future.
- The format of the manifest file
- Faster immutable-based undefined value removal (`removeUndefined` replaced with
  `withoutUndefined`)
- Major README rewrite to document the new changes
- Updated dependencies

### Removed

- `WebPictureStyles.ts`, its code was already merged with the react example.

## [2.1.2] - 2019-03-29

### Fixed

- Forgot the `bin` field in package.json, CLI is now usable

## [2.1.1] - 2019-03-23

### Fixed

- WebP optimization
- Typos

## [2.1.0] - 2019-03-23

`imagemin-webp` integration was scrapped as the binary seems to be buggy. The cwebp-bin would
corrupt images with alpha channels, probably due to an incompatibility with `libvips`.

Instead, the quality for `libvips` WebP was reduced to match `imagemin-webp` sizes (q=70).

### Added

- Better WebP optimization
- TIFF support
- `convertFormat` option, for codec conversion
- `exportOriginal` option, for only WebP exports
- More Typescript typings
- Better error codes + documentation

### Fixed

- The "pass-through optimizer function" wasn't returning a promise
- Dual-exports of originally .webp images, causing an error

## [2.0.5] - 2019-03-23

### Changed

- Updated all dependencies. Some now require Node.js 8

### Fixed

- Absolute paths on Windows (tiny-glob bug)

## [2.0.4] - 2019-03-20

### Fixed

- README typos
- Formatted the CHANGELOG

## [2.0.3] - 2019-03-20

### Fixed

- Fixed README layout
- npms.io should now see badges for scoring

## [2.0.2] - 2019-03-20

### Added

- Started keeping a changelog
- semantic-release integration with Travis CI for automatic deployment to GitHub and NPM

### Removed

- standard-version (and other version-related package.json scripts)

### Changed

- docs:(readme) will now trigger a patch release

### Fixed

- Badges are now recognized by the npms.io scoring algorithm

## [2.0.1] - 2019-03-16

### Changed

- Improved README
- Fixed links
- Added new demo image

### Fixed

- Absolute path conflict with `tiny-glob`

## [2.0.0] - 2019-03-16

#### Responsive Image Builder has been re-written from the ground up!

It took a while, but here it is! Bear in mind that this is a major update, introducing many BREAKING
CHANGES. The readme has been re-written, give it a quick check to see what's changed and how to use
the new API.

The TODO list has been extended with future goals, if you have another idea for improvement then why
not fork the project and submit a Pull Request?

### Added

- Typescript
- ES Module import support (tree-shaking is now "possible")
- More image optimizers
- Better documentation
- TODO list
- Travis CI script

### Changed

- Better configuration
- Better performance with Node.js streams

## [1.1.3] - 2018-11-11

### Fixed

- Fixed bug where GIFs would fail to copy from nested directories

## [1.1.2] - 2018-11-08

### Changed

- Use `fs-extra` in favour of `fs`

### Fixed

- Fix bug on UNIX systems when copying from nested directories

## [1.1.1] - 2018-11-04

### Added

- Angular example on how to use the library

## [1.1.0] - 2018-11-04

### Added

- Image optimization

## [1.0.3] - 2018-11-03

First release

[unreleased]: https://github.com/marcuscemes/image-processing-pipeline/compare/v4.0.0...HEAD
[4.0.0]: https://github.com/marcuscemes/image-processing-pipeline/compare/v3.1.3...v4.0.0
[3.1.3]: https://github.com/marcuscemes/image-processing-pipeline/compare/v3.1.1...v3.1.3
[3.1.1]: https://github.com/marcuscemes/image-processing-pipeline/compare/v3.1.0...v3.1.1
[3.1.0]: https://github.com/marcuscemes/image-processing-pipeline/compare/v3.0.1...v3.1.0
[3.0.1]: https://github.com/marcuscemes/image-processing-pipeline/compare/v3.0.0...v3.0.1
[3.0.0]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.1.2...v3.0.0
[2.1.2]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.1.1...v2.1.2
[2.1.1]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.1.0...v2.1.1
[2.1.0]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.0.5...v2.1.0
[2.0.5]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.0.4...v2.0.5
[2.0.4]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.0.3...v2.0.4
[2.0.3]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.0.2...v2.0.3
[2.0.2]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.0.1...v2.0.2
[2.0.1]: https://github.com/marcuscemes/image-processing-pipeline/compare/v2.0.0...v2.0.1
[2.0.0]: https://github.com/marcuscemes/image-processing-pipeline/compare/v1.1.3...v2.0.0
[1.1.3]: https://github.com/marcuscemes/image-processing-pipeline/compare/v1.1.2...v1.1.3
[1.1.2]: https://github.com/marcuscemes/image-processing-pipeline/compare/v1.1.1...v1.1.2
[1.1.1]: https://github.com/marcuscemes/image-processing-pipeline/compare/v1.1.0...v1.1.1
[1.1.0]: https://github.com/marcuscemes/image-processing-pipeline/compare/v1.0.3...v1.1.0
[1.0.3]: https://github.com/marcuscemes/image-processing-pipeline/compare/v0.0.1...v1.0.3

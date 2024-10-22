[![CI](https://github.com/jtdLab/build_semver/workflows/CI/badge.svg?branch=master)](https://github.com/jtdLab/build_semver/actions?query=workflow%3ACI+branch%3Amaster)
[![Pub Package](https://img.shields.io/pub/v/build_semver.svg)](https://pub.dev/packages/build_semver)
[![package publisher](https://img.shields.io/pub/publisher/build_semver.svg)](https://pub.dev/packages/build_semver/publisher)

Include the version of your package in our source code.

1. Add `build_semver` to `pubspec.yaml`. Also make sure there is a `version`
   field.

   ```yaml
   name: my_pkg
   version: 1.2.3
   dev_dependencies:
     build_runner: ^1.0.0
     build_semver: ^2.0.0
   ```

2. Run a build.

   ```console
   > dart pub run build_runner build
   ```

   `lib/src/version.dart` will be generated with content:

   ```dart
   // Generated code. Do not modify.
   import 'package:pub_semver/pub_semver.dart';

   final packageVersion = Version.parse('1.2.3');
   ```

To change the path of the generated file, create a
[`build.yaml`](https://pub.dev/packages/build_config) in the root of your
package. By changing the `output` option of this builder, the path can be
customized:

```yaml
targets:
  $default:
    builders:
      build_semver:
        options:
          output: lib/src/custom/path/to/version.dart
```

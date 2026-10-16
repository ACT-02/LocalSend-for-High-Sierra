LocalSend for High Sierra is an unofficial backport of [LocalSend](https://github.com/localsend/localsend) for Intel Macs running macOS High Sierra 10.13.6.

It tracks official LocalSend releases and publishes a High Sierra x86_64 build when the compatibility checks pass.

The backport restores macOS 10.13-compatible runtime paths in FlutterMacOS and the Dart VM, provides compatibility for newer Objective-C and Metal APIs, fixes Swift runtime loading for High Sierra, compiles Native Assets with a real 10.13 deployment target, and includes High Sierra-specific shims for affected plugins and the macOS ShareExtension.
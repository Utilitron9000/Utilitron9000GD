# Utilitron9000

This repo will contain the GDNative library that loads Utilitron and provides an API to GDScript.

It may also contain the editor tools for defining AI behaviours

## Requirements
To compile the library you will need a C compiler like clang as well as (scons)[https://scons.org/]
To use it, you will also need the latest Godot binary.

## Compiling the library

1. Create a new directory `GDNativeLibs`
2. Navigate to this new directory `cd GDNativeLibs` 
3. Clone this repo
4. Clone the godot_headers `git clone https://github.com/GodotNativeTools/godot_headers.git`
5. `cd Utilitron9000GD`
6. `scons platform=<yourplatform>` where `<yourplatform>` is `windows`, `osx`, or `linux`

## Adding the library to your Godot project

1. Create a `/lib` directory at the root of your project
2. Copy both `utilitronGD.gdnlib` and the compiled library file (`.dylib`, `.so`, or `.dll` depending on your platform) into the lib directory
3. Create a new resource in Godot, and choose NativeScript (.gdns) as the resource type and `utilitron` as the name
4. Enter `UTILITRON` in this NativeScript's class name field 
5. Select utilitronGD.gdnlib as the library for this script

## Accessing from GDScript

`FIXME We should make our library a singleton so that we do not have to manage multiple instances or use .new()`
1. Add `var utilitron = preload("res://lib/utilitron.gdns").new()`
2. Call some utilitron method i.e. `utilitron.get_data()`


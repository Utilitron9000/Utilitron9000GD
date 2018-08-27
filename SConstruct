#!python

import os, subprocess

#Local dependencies
godot_headers_path = ARGUMENTS.get("headers", os.getenv("GODOT_HEADERS", "../godot_headers/"))

target = ARGUMENTS.get("target", "debug")

platform = ARGUMENTS.get("p", "linux")
platform = ARGUMENTS.get("platform", platform)

env = Environment()
if platform == "windows":
    env = Environment(ENV = os.environ)

if ARGUMENTS.get("use_llvm", "no") == "yes":
    env["CC"] = "clang"

def add_sources(sources, directory):
    for file in os.listdir(directory):
        if file.endswith('.c'):
            sources.append(directory + '/' + file)

if platform == 'osx':
    env.Append(CCFLAGS = ['-g', '-O3', '-arch', 'x86_64'])
    env.Append(LINKFLAGS = ['-arch', 'x86_64'])

if platform == 'linux':
    env.Append(CCFLAGS = ['-g', '-fPIC', '-O3', '-std=c11'])

if platform == "windows":
    if target == "debug":
        env.Append(CCFLAGS = ['-EHsc', '-D_DEBUG', '/MDd'])
    else:
        env.Append(CCFLAGS = ['-O2', '-EHsc', '-DNDEBUG', '/MD'])

# , 'include', 'include/core'
env.Append(CPPPATH=['.', godot_headers_path])

sources = []
add_sources(sources, "src")

library = env.SharedLibrary(target='bin/utilitronGD', source=sources)
Default(library)

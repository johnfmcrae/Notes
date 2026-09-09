# Building with CMake

The most basic way to build with CMake is to set up and build with these commands:

```bash
cmake -B build
cmake --build build
```

In the first line, the `-B` flag is asking CMake to put all the generated files and artifacts from the current build location (location you're running the command) into the `build` folder. The second command runs the build.

## Debug versus Release

You can specify the build target in CMake using

```bash
-DCMAKE_BUILD_TYPE=Debug
```

## Adding Jobs

You can specify the number of jobs (roughly, CPU cores) that make uses with the `-j` option. So for two jobs, use,

```bash
cmake --build build -j2
```

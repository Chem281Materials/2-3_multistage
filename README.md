# Multi-Stage Docker Deployment of MOPAC

## Task 1

You have previously used Docker to create a deployment image for MOPAC.
**You will now create a new deployment image for MOPAC, with the additional requirement that it must use a multi-stage build process.**

The GitHub repository for MOPAC is available [here](https://github.com/openmopac/mopac). Note that although there are already Docker containers available for MOPAC, yours must conform to the following constraints: (1) it must use the `ubuntu:26.04` image as its base; (2) it must build MOPAC from source, using CMake (the MOPAC documentation in the `README.md` file linked above describes how to build MOPAC using CMake); (3) it must be possible for the end-user to run MOPAC with the following command:

```
docker run --rm -v <volume_options> <image_name> <input_file_name>
```

Follow best practices for container development.
**In addition, the image must be built with a multi-stage build, which should be competently designed to minimize the size of the image.**
Your final stage should not use `apt`, `apt-get`, or a similar package manager at all. 
You may reuse as much code from your previous MOPAC deployment image as you wish.

To find the Ubuntu package names for software dependencies that you want to install with `apt-get`, you can use the [Ubuntu Packages Search](https://packages.ubuntu.com/).
For packages with short name abbreviations (such as BLAS), you may want to select the “Search on: Descriptions” option and search for the full name of the library.
You can also usually find the information you need through a more general web search.
Pay careful attention to the CMake output; if something goes wrong, it will usually give you a hint regarding what you need to do.
As an example input file, you can use the following (save it into a file with a “`.mop`” extension).
The normal way to run a MOPAC input file is “`mopac <file_name>.mop`”.

```
AM1
Formic acid
Example of normal geometry definition
O
C 1.20 1
O 1.32 1 116.8 1 0.0 0 2 1
H 0.98 1 123.9 1 0.0 0 3 2 1
H 1.11 1 127.3 1 180.0 0 2 1 3
0 0.00 0 0.0 0 0.0 0 0 0 0
```
## Task 2

Put all of your files (including your Dockerfile, entrypoint script, test input file, etc.) in this GitHub repository.
Create a GitHub Actions workflow in this repository that runs a MOPAC calculation through your image and prints the output from the **host**.

## Task 3

In the Answer section below, provide the size of your previous image, as well as the size of the new multi-stage image.
Unless you had originally used a multi-stage build, you will likely find that the new image is dramatically smaller.

Briefly (in roughly 3-5 sentences) describe the primary reasons for the differences in size - for example, which directories are the primary source of bloat in the larger image?
You don't need to provide an exhaustive description of every difference, but list a few noteworthy specifics.
If your original submission used a multi-stage build, you can simply indicate this fact in liue of a description.

## Answer

Provide your response to Task 3 here.

## Hints

If you understand the lecture material regarding libraries, you will find that this doesn't actually require much effort.
Think carefully about what an executable actually needs at runtime.

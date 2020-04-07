# `lanibase`

`lanibase` is the base Docker image used by Project Laniakea.
It contains a special `selfadd` program and an `entrypoint` script to
enable running the container as a named non-root user.
This makes `lanibase`-based containers behave like Singularity
containers and useful for (interactive) data analysis.

`selfadd` checks the current `uid` and add the necessary information
to `/etc/passwd` and `/etc/group`.
Therefore, to run `lanibase`-based images as a named non-root user,
use

    docker run --rm -it -u $(id -u):$(id -g) -e USER=$(whoami) laniakeasrc/lanibase:20200327

Images that build on `lanibase`, if override the entrypoint, should
use an entrypoint script similar to `lanibase`'s.
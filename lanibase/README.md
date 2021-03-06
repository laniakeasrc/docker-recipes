# [`lanibase`][1]

[`lanibase`][1] is the base Docker image used by Project Laniakea.
It contains a special `selfadd` program and an `entrypoint` script to
enable running the container as a named non-root user.
This makes `lanibase`-based containers behave like Singularity
containers and useful for (interactive) data analysis.

`selfadd` checks the current `uid` and add the necessary information
to `/etc/passwd` and `/etc/group`.
Therefore, to run `lanibase`-based images as a named non-root user,
use

    l6a lanibase [args]

Images that build on `lanibase`, if override the entrypoint, should
use an entrypoint script similar to `lanibase`'s.

## Releases

[`l6acon/lanibase`][1] tags | `debian` tag | `debian` digest
--- | --- | ---
`10.6`, `20201117`, `10`, `buster`, `latest` | `buster-20201117-slim` | `sha256:bb5473161a03d24b397c46778e58f845e29f1ce42a2953666ef8289f00afda42`
`10.5`, `20200908`                           | `buster-20200908-slim` | `sha256:8d81110c3f93a777e3f4053a6b18b70e4a1003655b8c2664bdf18b19043f99d9`
`10.4`, `20200720`                           | `buster-20200720-slim` | `sha256:79326248a982be0b36e8280f906916fceffdd5c17a298b14446e5e72cc822fe7`
`10.3`, `20200422`                           | `buster-20200422-slim` | `sha256:9d08b5e6b5f23a61634da3d08d654a24b06946f4ef7f6dd8b75e52c6baa1f1b0`
`10.2`, `20200130`                           | `buster-20200130-slim` | `sha256:9ab269df3cfa21324fcbfcf5366722d99d77ab480a8cbb0727612f7ea4e6ae27`
`10.1`, `20191014`                           | `buster-20191014-slim` | `sha256:11253793361a12861562d1d7b15b8b7e25ac30dd631e3d206ed1ca969bf97b7d`

Note that `lanibase`'s "release tags", e.g., `10.2`, have different
meaning than `debian`'s point release versions.
For `debian`, the
[point release versions](https://wiki.debian.org/DebianReleases/PointReleases)
are defined at the release time.
However, `lanibase` images are based on
[official `debian` Docker images](https://hub.docker.com/_/debian),
which are freezes of the rolling releases.
Because the `debian:10.2` Docker image only got frozen at
`debian:buster-20191014-slim`, which is closer to the `debian` 10.2
point release, there is a time lag between the same versions of
`debian` Docker images and point releases.
This time lag is carried over to `lanibase`.

[1]: https://hub.docker.com/repository/docker/l6acon/lanibase

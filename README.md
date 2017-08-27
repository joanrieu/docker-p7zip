# docker-p7zip
Docker container to pack/unpack archives using p7zip

## Usage

You can use the following flags to give the container access to your files.

| `docker run` flag | Description                                      |
|-------------------|--------------------------------------------------|
| `-u uid:gid`      | set the correct permissions inside the container |
| `-v ...:/data`    | mount a folder as the default workdir            |

The container's entrypoint is the `7z` executable.
Here are the available commands taken from the [man page](https://linux.die.net/man/1/7z) (emphasis mine).

| `7z` command | Description                 |
|--------------|-----------------------------|
| `a`          | **Add**                     |
| `d`          | Delete                      |
| `e`          | Extract                     |
| `l`          | **List**                    |
| `t`          | **Test**                    |
| `u`          | Update                      |
| `x`          | **eXtract with full paths** |

## Examples

### Listing the contents of an archive

    docker run --rm -it \
      -u 500:500 \
      -v $(pwd):/data \
      joanrieu/p7zip \
        l my-archive.zip

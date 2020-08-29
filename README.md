# asdf-docker

This is my current easy-to-setup development environment based on ArchLinux.

## Usage

### If you want a nodejs environment run...

```bash
$ docker run -it -v ~/Developer:/Developer allangarcia/asdf-nodejs
```

_where: **~/Developer** is any directory you want to develop on your local computer, and
**/Developer** is the directory mounted inside the container._

### If you want a rails environment run...

```bash
$ docker run -it -v ~/Developer:/Developer allangarcia/asdf-rails
```

## -p to export ports

You'll generally use this together with -p 3000:3000 or any other port you want to export

I personally use also with --rm to remove the container when I leave.

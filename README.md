# develop-on-docker

A set of Docker images to aid development in containers

## Current Images

- [`develop-base`][develop-base] - extended base image with common tools
- [`develop-php`][develop-php] - PHP 5.6 development environment
- [`develop-haskell`][develop-haskell] - Haskell (GHC) development environment
- [`develop-dotnet`][develop-dotnet] - .NET core development environment with `dotnet` CLI
- [`develop-rust`][develop-rust] - Rust development environment via `rustup.sh`
- [`develop-elixir`][develop-elixir] - Elixir/Erlang development environment
- [`develop-node`][develop-node] - NodeJS 6.2.0 development environment
- [`develop-elm`][develop-elm] - Elm development environment
- [`develop-racket`][develop-racket] - Racket 6.5 development environment with the main distribution of packages
- [`develop-clojure`][develop-clojure] - Clojure development environment with Open JDK 7, Leiningen, and Drip

## Usage

These images can be run with plain ol' `docker`:

```
$ docker run --rm -it slogsdon/develop-base
```

and with `docker-compose` as another service:

```yaml
version: '2'
services:
  # ...
  develop:
    image: slogsdon/develop-base
    volumes:
      - ~/.dotfiles:/home/user/.dotfiles
      - ./:/home/user/code
```

```
$ docker-compose run develop
```

## Configuring

These images do not supply any dotfiles for configuring applications, so plan to use Docker volumes for this purpose, similar to the Docker Compose example above. If you already have a dotfiles folder in use on your development machines, create a volume for them at `/home/user/.dotfiles`, and if needed and present, a setup script located at `/home/user/.dotfiles/scripts/install.sh` will be run (GNU `stow` is available for convenience).

## License

See [LICENSE](https://github.com/slogsdon/develop-on-docker/blob/master/LICENSE).

[develop-base]: https://hub.docker.com/r/slogsdon/develop-base/
[develop-php]: https://hub.docker.com/r/slogsdon/develop-php/
[develop-haskell]: https://hub.docker.com/r/slogsdon/develop-haskell/
[develop-dotnet]: https://hub.docker.com/r/slogsdon/develop-dotnet/
[develop-rust]: https://hub.docker.com/r/slogsdon/develop-rust/
[develop-elixir]: https://hub.docker.com/r/slogsdon/develop-elixir/
[develop-node]: https://hub.docker.com/r/slogsdon/develop-node/
[develop-elm]: https://hub.docker.com/r/slogsdon/develop-elm/
[develop-racket]: https://hub.docker.com/r/slogsdon/develop-racket/
[develop-clojure]: https://hub.docker.com/r/slogsdon/develop-clojure/

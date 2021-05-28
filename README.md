# DaCHS on Docker - server+postgres compose

### Prologue: about dachs-on-docker repositories

Analogous to [gavodachs/docker-dachs](github.com/gavodachs/docker-dachs), 
this repository also contains the files for encapsulating [GAVO DaCHS](http://docs.g-vo.org/DaCHS/)
in Docker containers.

> The difference between _this_ and other repo regards how the DaCHS suite (server+database)
> is arranged inside Docker. _Here_, the server (dachs) is separated from the database (postgres)
> on their own containers and are put to work together through _docker-compose_.
> 
> * _If you want to use Dachs on Docker in a production environment, this is what you want -- at least, where you want to start._

You'll find the corresponding images under ['gavodachs'][4] DockerHub organization repositories (`server`, `postgres`).

> If you have already used _DaCHS-on-Docker_ before you may have pulled the images from `chbrandt/dachs` repository,
> they are still there for your convenience, but slowly moving  to `gavodachs` repos (versions 2+).

[![Build Status](https://travis-ci.org/gavodachs/docker-dachs-compose.svg?branch=master)](https://travis-ci.org/gavodachs/docker-dachs-compose)

---

DaCHS -- the service -- is composed by two daemons: PostgreSQL and the DaCHS
server itself. Postgres stores the data, whereas DaCHS-server interfaces the
data-store and the user and everything related to [Virtual Observatory](http://ivoa.net/).

The [dockerfiles](dockerfiles) in here will setup image families (with their respective tags):
* `gavodachs/server`: the DaCHS data-manager/server suite
* `gavodachs/postgres`: the Postgres db used by DaCHS

For detailed information on DaCHS itself or Docker, please
visit their official documentation, [DaCHS/docs][1] or [Docker/docs][2].


# Run

To run the suite using `docker-compose` is straightforward:
```bash
$ docker-compose up
```

This will pull the images defined in [`docker-compose.yml`](docker-compose.yml),
* `gavodachs/server`: the DaCHS data-manager/server suite
* `gavodachs/postgres`: the Postgres db used by DaCHS
, and run them all at once.

After a couple of seconds you should be able to see DaCHS web page at http://localhost:8080 .


# Build

If you want to build fresh versions of DaCHS and Postgres you can do that with `docker-compose` too:
```bash
$ docker-compose build
```

And then proceed to run it, should give you a fresh Dachs suite running in no time.

[1]: http://dachs-doc.readthedocs.io
[2]: https://docs.docker.com/
[4]: https://hub.docker.com/repository/docker/gavodachs


/.\

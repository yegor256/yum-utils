[![Build Status](https://img.shields.io/travis/yegor256/yum-utils/master.svg)](https://travis-ci.org/yegor256/yum-utils)
[![Docker Cloud Automated build](https://img.shields.io/docker/cloud/automated/yegor256/yum-utils)](https://hub.docker.com/r/yegor256/yum-utils)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/yegor256/yum-utils/master/LICENSE.txt)

Developers tools to test
[`yum`](https://en.wikipedia.org/wiki/Yum_%28software%29) and
[`rpm`](https://en.wikipedia.org/wiki/RPM_Package_Manager).

For example, you want to create an RPM repository. You create
a directory (say, `/home/yegor/repo`) and place all your
[`.rpm` files](https://rpm-packaging-guide.github.io/) there.
Then, you execute
[`createrepo`](https://linux.die.net/man/8/createrepo) to create
meta files:

```
$ docker run --rm -v /home/yegor/repo:/repo yegor256/yum-utils createrepo /repo
```

Then, you may want to list all artifacts in the repo at `/home/yegor/repo`:

```
$ docker run --rm -v /home/yegor/repo:/repo yegor256/yum-utils \
  /bin/bash -c "yum-config-manager --add-repo file:///repo; \
  yum --disablerepo='*' --enablerepo='repo' list available"
```

Should work.

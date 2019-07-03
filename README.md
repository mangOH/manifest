# repo manifest repository for mangOH

This repository is a fork of ssh://gerrit.legato.io:29418/manifest which adds mangOH specific
manifests.  Currently only WP76xx on mangOH Yellow is supported by
`mangOH/branches/master/wp76xx.xml`

Currently there is a tag missing in the `yocto-downloads` repository, so it's necessary to run:
To use this manifest, do:
1. `mkdir yocto-mangoh`
1. `cd yocto-mangoh`
1. `repo init -g default,-cache -m mangOH/branches/master/wp76xx.xml --manifest-url=https://github.com/mangOH/manifest.git`
1. `repo sync`
1. `make image_bin && make toolchain_bin`

If you want to ensure that you build yocto in an appropriate environment, you can add
`USE_DOCKER=1` before the `make` commands.  The `-cache` in the `repo init` command disables
fetching of repositories in the "cache" group.  This is necessary because the `yocto-downloads`
repository is missing the `SWI9X07Y_02.28.03.01` tag.

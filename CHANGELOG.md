# Changelog

## 0.6.5 (2013-10-29)
+ Runtime: Containers can now be named
+ Runtime: Containers can now be linked together for service discovery
+ Runtime: 'run -a', 'start -a' and 'attach' can forward signals to the container for better integration with process supervisors
+ Runtime: Automatically start crashed containers after a reboot
+ Runtime: Expose IP, port, and proto as separate environment vars for container links
* Runtime: Allow ports to be published to specific ips
* Runtime: Prohibit inter-container communication by default
* Documentation: Fix the flags for nc in example
- Client: Only pass stdin to hijack when needed to avoid closed pipe errors
* Testing: Remove warnings and prevent mount issues
* Client: Use less reflection in command-line method invocation
- Runtime: Ignore ErrClosedPipe for stdin in Container.Attach
- Testing: Change logic for tty resize to avoid warning in tests
- Client: Monitor the tty size after starting the container, not prior
- Hack: Update install.sh with $sh_c to get sudo/su for modprobe
- Client: Remove useless os.Exit() calls after log.Fatal
* Hack: Update all the mkimage scripts to use --numeric-owner as a tar argument
* Hack: Update hack/release.sh process to automatically invoke hack/make.sh and bail on build and test issues
+ Hack: Add initial init scripts library and a safer Ubuntu packaging script that works for Debian
- Runtime: Fix untag during removal of images 
- Runtime: Remove unused field kernelVersion 
* Hack: Add -p option to invoke debootstrap with http_proxy
- Builder: Fix race condition in docker build with verbose output
- Registry: Fix content-type for PushImageJSONIndex method
* Runtime: Fix issue when mounting subdirectories of /mnt in container
* Runtime: Check return value of syscall.Chdir when changing working directory inside dockerinit
* Contrib: Improve helper tools to generate debian and Arch linux server images

## 0.6.4 (2013-10-16)
- Runtime: Add cleanup of container when Start() fails
- Testing: Catch errClosing error when TCP and UDP proxies are terminated
- Testing: Add aggregated docker-ci email report
- Testing: Remove a few errors in tests
* Contrib: Reorganize contributed completion scripts to add zsh completion
* Contrib: Add vim syntax highlighting for Dockerfiles from @honza
* Runtime: Add better comments to utils/stdcopy.go
- Testing: add cleanup to remove leftover containers
* Documentation: Document how to edit and release docs
* Documentation: Add initial draft of the Docker infrastructure doc
* Contrib: Add mkimage-arch.sh
- Builder: Abort build if mergeConfig returns an error and fix duplicate error message
- Runtime: Remove error messages which are not actually errors
* Testing: Only run certain tests with TESTFLAGS='-run TestName' make.sh
* Testing: Prevent docker-ci to test closing PRs
- Documentation: Minor updates to postgresql_service.rst
* Testing: Add nightly release to docker-ci
* Hack: Improve network performance for VirtualBox
* Hack: Add vagrant user to the docker group
* Runtime: Add utils.Errorf for error logging
- Packaging: Remove deprecated packaging directory
* Hack: Revamp install.sh to be usable by more people, and to use official install methods whenever possible (apt repo, portage tree, etc.)
- Hack: Fix contrib/mkimage-debian.sh apt caching prevention
* Documentation: Clarify LGTM process to contributors
- Documentation: Small fixes to parameter names in docs for ADD command
* Runtime: Record termination time in state.
- Registry: Use correct auth config when logging in.
- Documentation: Corrected error in the package name
* Documentation: Document what `vagrant up` is actually doing
- Runtime: Fix `docker rm` with volumes
- Runtime: Use empty string so TempDir uses the OS's temp dir automatically
- Runtime: Make sure to close the network allocators
* Testing: Replace panic by log.Fatal in tests
+ Documentation: improve doc search results
- Runtime: Fix some error cases where a HTTP body might not be closed
* Hack: Add proper bash completion for "docker push"
* Documentation: Add devenvironment link to CONTRIBUTING.md
* Documentation: Cleanup whitespace in API 1.5 docs
* Documentation: use angle brackets in MAINTAINER example email
- Testing: Increase TestRunDetach timeout
* Documentation: Fix help text for -v option
+ Hack: Added Dockerfile.tmLanguage to contrib
+ Runtime: Autorestart containers by default
* Testing: Adding more tests around auth.ResolveAuthConfig
* Hack: Configured FPM to make /etc/init/docker.conf a config file
* Hack: Add xz utils as a runtime dep
* Documentation: Add `apt-get install curl` to Ubuntu docs
* Documentation: Remove Gentoo install notes about #1422 workaround
* Documentation: Fix Ping endpoint documentation
* Runtime: Bump vendor kr/pty to commit 3b1f6487b (syscall.O_NOCTTY)
* Runtime: lxc: Allow set_file_cap capability in container
* Documentation: Update archlinux.rst
- Documentation: Fix ironic typo in changelog
* Documentation: Add explanation for export restrictions
* Hack: Add cleanup/refactor portion of #2010 for hack and Dockerfile updates
+ Documentation: Changes to a new style for the docs. Includes version switcher.
* Documentation: Formatting, add information about multiline json
+ Hack: Add contrib/mkimage-centos.sh back (from #1621), and associated documentation link
- Runtime: Fix panic with wrong dockercfg file
- Runtime: Fix the attach behavior with -i
* Documentation: Add .dockercfg doc
- Runtime: Move run -rm to the cli only
* Hack: Enable SSH Agent forwarding in Vagrant VM
+ Runtime: Add -rm to docker run for removing a container on exit
* Documentation: Improve registry and index REST API documentation
* Runtime: Split stdout stderr
- Documentation: Replace deprecated upgrading reference to docker-latest.tgz, which hasn't been updated since 0.5.3
* Documentation: Update Gentoo installation documentation now that we're in the portage tree proper
- Registry: Fix the error message so it is the same as the regex
* Runtime: Always create a new session for the container
* Hack: Add several of the small make.sh fixes from #1920, and make the output more consistent and contributor-friendly
* Documentation: Various command fixes in postgres example
* Documentation: Cleanup and reorganize docs and tooling for contributors and maintainers
- Documentation: Minor spelling correction of protocoll -> protocol
* Hack: Several small tweaks/fixes for contrib/mkimage-debian.sh
+ Hack: Add @tianon to hack/MAINTAINERS

## 0.6.3 (2013-09-23)
* Packaging: Update tar vendor dependency
- Client: Fix detach issue
- Runtime: Only copy and change permissions on non-bindmount volumes
- Registry: Update regular expression to match index
* Runtime: Allow multiple volumes-from
* Packaging: Download apt key over HTTPS
* Documentation: Update section on extracting the docker binary after build
* Documentation: Update development environment docs for new build process
* Documentation: Remove 'base' image from documentation
* Packaging: Add 'docker' group on install for ubuntu package
- Runtime: Fix HTTP imports from STDIN

## 0.6.2 (2013-09-17)
+ Hack: Vendor all dependencies
+ Builder: Add -rm option in order to remove intermediate containers
+ Runtime: Add domainname support
+ Runtime: Implement image filtering with path.Match
* Builder: Allow multiline for the RUN instruction
* Runtime: Remove unnecesasry warnings
* Runtime: Only mount the hostname file when the config exists
* Runtime: Handle signals within the `docker login` command
* Runtime: Remove os/user dependency
* Registry: Implement login with private registry
* Remote API: Bump to v1.5
* Packaging: Break down hack/make.sh into small scripts, one per 'bundle': test, binary, ubuntu etc.
* Documentation: General improvements
- Runtime: UID and GID are now also applied to volumes
- Runtime: `docker start` set error code upon error
- Runtime: `docker run` set the same error code as the process started
- Registry: Fix push issues

## 0.6.1 (2013-08-23)
* Registry: Pass "meta" headers in API calls to the registry
- Packaging: Use correct upstart script with new build tool
- Packaging: Use libffi-dev, don't build it from sources
- Packaging: Removed duplicate mercurial install command

## 0.6.0 (2013-08-22)
- Runtime: Load authConfig only when needed and fix useless WARNING
+ Runtime: Add lxc-conf flag to allow custom lxc options
- Runtime: Fix race conditions in parallel pull
- Runtime: Improve CMD, ENTRYPOINT, and attach docs.
* Documentation: Small fix to docs regarding adding docker groups
* Documentation: Add MongoDB image example
+ Builder: Add USER instruction do Dockerfile
* Documentation: updated default -H docs
* Remote API: Sort Images by most recent creation date.
+ Builder: Add workdir support for the Buildfile
+ Runtime: Add an option to set the working directory
- Runtime: Show tag used when image is missing
* Documentation: Update readme with dependencies for building
* Documentation: Add instructions for creating and using the docker group
* Remote API: Reworking opaque requests in registry module
- Runtime: Fix Graph ByParent() to generate list of child images per parent image.
* Runtime: Add Image name to LogEvent tests
* Documentation: Add sudo to examples and installation to documentation
+ Hack: Bash Completion: Limit commands to containers of a relevant state
* Remote API: Add image name in /events
* Runtime: Apply volumes-from before creating volumes
- Runtime: Make docker run handle SIGINT/SIGTERM
- Runtime: Prevent crash when .dockercfg not readable
* Hack: Add docker dependencies coverage testing into docker-ci
+ Runtime: Add -privileged flag and relevant tests, docs, and examples
+ Packaging: Docker-brew 0.5.2 support and memory footprint reduction
- Runtime: Install script should be fetched over https, not http.
* Packaging: Add new docker dependencies into docker-ci
* Runtime: Use Go 1.1.2 for dockerbuilder
* Registry: Improve auth push
* Runtime: API, issue 1471: Use groups for socket permissions
* Documentation: PostgreSQL service example in documentation
* Contrib: bash completion script
* Tests: Improve TestKillDifferentUser to prevent timeout on buildbot
* Documentation: Fix typo in docs for docker run -dns
* Documentation: Adding a reference to ps -a
- Runtime: Correctly detect IPv4 forwarding
- Packaging: Revert "docker.upstart: avoid spawning a `sh` process"
* Runtime: Use ranged for loop on channels
- Runtime: Fix typo: fmt.Sprint -> fmt.Sprintf
- Tests: Fix typo in TestBindMounts (runContainer called without image)
* Runtime: add websocket support to /container/<name>/attach/ws
* Runtime: Mount /dev/shm as a tmpfs
- Builder: Only count known instructions as build steps
- Builder: Fix docker build and docker events output
- Runtime: switch from http to https for get.docker.io
* Tests: Improve TestGetContainersTop so it does not rely on sleep
+ Packaging: Docker-brew and Docker standard library
* Testing: Add some tests in server and utils
+ Packaging: Release docker with docker
- Builder: Make sure ENV instruction within build perform a commit each time
* Packaging: Fix the upstart script generated by get.docker.io
- Runtime: fix small \n error un docker build
* Runtime: Let userland proxy handle container-bound traffic
* Runtime: Updated the Docker CLI to specify a value for the "Host" header.
* Runtime: Add warning when net.ipv4.ip_forwarding = 0
* Registry: Registry unit tests + mock registry
* Runtime: fixed #910. print user name to docker info output
- Builder: Forbid certain paths within docker build ADD
- Runtime: change network range to avoid conflict with EC2 DNS
* Tests: Relax the lo interface test to allow iface index != 1
* Documentation: Suggest installing linux-headers by default.
* Documentation: Change the twitter handle
* Client: Add docker cp command and copy api endpoint to copy container files/folders to the host
* Remote API: Use mime pkg to parse Content-Type
- Runtime: Reduce connect and read timeout when pinging the registry
* Documentation: Update amazon.rst to explain that Vagrant is not necessary for running Docker on ec2
* Packaging: Enabled the docs to generate manpages.
* Runtime: Parallel pull
- Runtime: Handle ip route showing mask-less IP addresses
* Documentation: Clarify Amazon EC2 installation
* Documentation: 'Base' image is deprecated and should no longer be referenced in the docs.
* Runtime: Fix to "Inject dockerinit at /.dockerinit"
* Runtime: Allow ENTRYPOINT without CMD
- Runtime: Always consider localhost as a domain name when parsing the FQN repos name
* Remote API: 650 http utils and user agent field
* Documentation: fix a typo in the ubuntu installation guide
- Builder: Repository name (and optionally a tag) in build usage
* Documentation: Move note about officially supported kernel
* Packaging: Revert "Bind daemon to 0.0.0.0 in Vagrant.
* Builder: Add no cache for docker build
* Runtime: Add hostname to environment
* Runtime: Add last stable version in `docker version`
- Builder: Make sure ADD will create everything in 0755
* Documentation: Add ufw doc
* Tests: Add registry functional test to docker-ci
- Documentation: Solved the logo being squished in Safari
- Runtime: Use utils.ParseRepositoryTag instead of strings.Split(name, ":") in server.ImageDelete
* Runtime: Refactor checksum
- Runtime: Improve connect message with socket error
* Documentation: Added information about Docker's high level tools over LXC.
* Don't read from stdout when only attached to stdin

## 0.5.3 (2013-08-13)
* Runtime: Use docker group for socket permissions
- Runtime: Spawn shell within upstart script
- Builder: Make sure ENV instruction within build perform a commit each time
- Runtime: Handle ip route showing mask-less IP addresses
- Runtime: Add hostname to environment

## 0.5.2 (2013-08-08)
 * Builder: Forbid certain paths within docker build ADD
 - Runtime: Change network range to avoid conflict with EC2 DNS
 * API: Change daemon to listen on unix socket by default

## 0.5.1 (2013-07-30)
 + API: Docker client now sets useragent (RFC 2616)
 + Runtime: Add `ps` args to `docker top`
 + Runtime: Add support for container ID files (pidfile like)
 + Runtime: Add container=lxc in default env
 + Runtime: Support networkless containers with `docker run -n` and `docker -d -b=none`
 + API: Add /events endpoint
 + Builder: ADD command now understands URLs
 + Builder: CmdAdd and CmdEnv now respect Dockerfile-set ENV variables
 * Hack: Simplify unit tests with helpers
 * Hack: Improve docker.upstart event
 * Hack: Add coverage testing into docker-ci
 * Runtime: Stdout/stderr logs are now stored in the same file as JSON
 * Runtime: Allocate a /16 IP range by default, with fallback to /24. Try 12 ranges instead of 3.
 * Runtime: Change .dockercfg format to json and support multiple auth remote
 - Runtime: Do not override volumes from config
 - Runtime: Fix issue with EXPOSE override
 - Builder: Create directories with 755 instead of 700 within ADD instruction

## 0.5.0 (2013-07-17)
 + Runtime: List all processes running inside a container with 'docker top'
 + Runtime: Host directories can be mounted as volumes with 'docker run -v'
 + Runtime: Containers can expose public UDP ports (eg, '-p 123/udp')
 + Runtime: Optionally specify an exact public port (eg. '-p 80:4500')
 + Registry: New image naming scheme inspired by Go packaging convention allows arbitrary combinations of registries
 + Builder: ENTRYPOINT instruction sets a default binary entry point to a container
 + Builder: VOLUME instruction marks a part of the container as persistent data
 * Builder: 'docker build' displays the full output of a build by default
 * Runtime: 'docker login' supports additional options
 - Runtime: Dont save a container's hostname when committing an image.
 - Registry: Fix issues when uploading images to a private registry

## 0.4.8 (2013-07-01)
 + Builder: New build operation ENTRYPOINT adds an executable entry point to the container.
 - Runtime: Fix a bug which caused 'docker run -d' to no longer print the container ID.
 - Tests: Fix issues in the test suite

## 0.4.7 (2013-06-28)
 * Registry: easier push/pull to a custom registry
 * Remote API: the progress bar updates faster when downloading and uploading large files
 - Remote API: fix a bug in the optional unix socket transport
 * Runtime: improve detection of kernel version
 + Runtime: host directories can be mounted as volumes with 'docker run -b'
 - Runtime: fix an issue when only attaching to stdin
 * Runtime: use 'tar --numeric-owner' to avoid uid mismatch across multiple hosts
 * Hack: improve test suite and dev environment
 * Hack: remove dependency on unit tests on 'os/user'
 + Documentation: add terminology section

## 0.4.6 (2013-06-22)
 - Runtime: fix a bug which caused creation of empty images (and volumes) to crash.

## 0.4.5 (2013-06-21)
 + Builder: 'docker build git://URL' fetches and builds a remote git repository
 * Runtime: 'docker ps -s' optionally prints container size
 * Tests: Improved and simplified
 - Runtime: fix a regression introduced in 0.4.3 which caused the logs command to fail.
 - Builder: fix a regression when using ADD with single regular file.

## 0.4.4 (2013-06-19)
 - Builder: fix a regression introduced in 0.4.3 which caused builds to fail on new clients.

## 0.4.3 (2013-06-19)
 + Builder: ADD of a local file will detect tar archives and unpack them
 * Runtime: Remove bsdtar dependency
 * Runtime: Add unix socket and multiple -H support
 * Runtime: Prevent rm of running containers
 * Runtime: Use go1.1 cookiejar
 * Builder: ADD improvements: use tar for copy + automatically unpack local archives
 * Builder: ADD uses tar/untar for copies instead of calling 'cp -ar'
 * Builder: nicer output for 'docker build'
 * Builder: fixed the behavior of ADD to be (mostly) reverse-compatible, predictable and well-documented.
 * Client: HumanReadable ProgressBar sizes in pull
 * Client: Fix docker version's git commit output
 * API: Send all tags on History API call
 * API: Add tag lookup to history command. Fixes #882
 - Runtime: Fix issue detaching from running TTY container
 - Runtime: Forbid parralel push/pull for a single image/repo. Fixes #311
 - Runtime: Fix race condition within Run command when attaching.
 - Builder: fix a bug which caused builds to fail if ADD was the first command
 - Documentation: fix missing command in irc bouncer example

## 0.4.2 (2013-06-17)
 - Packaging: Bumped version to work around an Ubuntu bug

## 0.4.1 (2013-06-17)
 + Remote Api: Add flag to enable cross domain requests
 + Remote Api/Client: Add images and containers sizes in docker ps and docker images
 + Runtime: Configure dns configuration host-wide with 'docker -d -dns'
 + Runtime: Detect faulty DNS configuration and replace it with a public default
 + Runtime: allow docker run <name>:<id>
 + Runtime: you can now specify public port (ex: -p 80:4500)
 * Client: allow multiple params in inspect
 * Client: Print the container id before the hijack in `docker run`
 * Registry: add regexp check on repo's name
 * Registry: Move auth to the client
 * Runtime: improved image removal to garbage-collect unreferenced parents
 * Vagrantfile: Add the rest api port to vagrantfile's port_forward
 * Upgrade to Go 1.1
 - Builder: don't ignore last line in Dockerfile when it doesn't end with \n
 - Registry: Remove login check on pull

## 0.4.0 (2013-06-03)
 + Introducing Builder: 'docker build' builds a container, layer by layer, from a source repository containing a Dockerfile
 + Introducing Remote API: control Docker programmatically using a simple HTTP/json API
 * Runtime: various reliability and usability improvements

## 0.3.4 (2013-05-30)
 + Builder: 'docker build' builds a container, layer by layer, from a source repository containing a Dockerfile
 + Builder: 'docker build -t FOO' applies the tag FOO to the newly built container.
 + Runtime: interactive TTYs correctly handle window resize
 * Runtime: fix how configuration is merged between layers
 + Remote API: split stdout and stderr on 'docker run'
 + Remote API: optionally listen on a different IP and port (use at your own risk)
 * Documentation: improved install instructions.

## 0.3.3 (2013-05-23)
 - Registry: Fix push regression
 - Various bugfixes

## 0.3.2 (2013-05-09)
 * Runtime: Store the actual archive on commit
 * Registry: Improve the checksum process
 * Registry: Use the size to have a good progress bar while pushing
 * Registry: Use the actual archive if it exists in order to speed up the push
 - Registry: Fix error 400 on push

## 0.3.1 (2013-05-08)
 + Builder: Implement the autorun capability within docker builder
 + Builder: Add caching to docker builder
 + Builder: Add support for docker builder with native API as top level command
 + Runtime: Add go version to debug infos
 + Builder: Implement ENV within docker builder
 + Registry: Add docker search top level command in order to search a repository
 + Images: output graph of images to dot (graphviz)
 + Documentation: new introduction and high-level overview
 + Documentation: Add the documentation for docker builder
 + Website: new high-level overview
 - Makefile: Swap "go get" for "go get -d", especially to compile on go1.1rc
 - Images: fix ByParent function
 - Builder: Check the command existance prior create and add Unit tests for the case
 - Registry: Fix pull for official images with specific tag
 - Registry: Fix issue when login in with a different user and trying to push
 - Documentation: CSS fix for docker documentation to make REST API docs look better.
 - Documentation: Fixed CouchDB example page header mistake
 - Documentation: fixed README formatting
 * Registry: Improve checksum - async calculation
 * Runtime: kernel version - don't show the dash if flavor is empty
 * Documentation: updated www.docker.io website.
 * Builder: use any whitespaces instead of tabs
 * Packaging: packaging ubuntu; issue #510: Use goland-stable PPA package to build docker

## 0.3.0 (2013-05-06)
 + Registry: Implement the new registry
 + Documentation: new example: sharing data between 2 couchdb databases
 - Runtime: Fix the command existance check
 - Runtime: strings.Split may return an empty string on no match
 - Runtime: Fix an index out of range crash if cgroup memory is not
 * Documentation: Various improvments
 * Vagrant: Use only one deb line in /etc/apt

## 0.2.2 (2013-05-03)
 + Support for data volumes ('docker run -v=PATH')
 + Share data volumes between containers ('docker run -volumes-from')
 + Improved documentation
 * Upgrade to Go 1.0.3
 * Various upgrades to the dev environment for contributors

## 0.2.1 (2013-05-01)
 + 'docker commit -run' bundles a layer with default runtime options: command, ports etc.
 * Improve install process on Vagrant
 + New Dockerfile operation: "maintainer"
 + New Dockerfile operation: "expose"
 + New Dockerfile operation: "cmd"
 + Contrib script to build a Debian base layer
 + 'docker -d -r': restart crashed containers at daemon startup
 * Runtime: improve test coverage

## 0.2.0 (2013-04-23)
 - Runtime: ghost containers can be killed and waited for
 * Documentation: update install intructions
 - Packaging: fix Vagrantfile
 - Development: automate releasing binaries and ubuntu packages
 + Add a changelog
 - Various bugfixes

## 0.1.8 (2013-04-22)
 - Dynamically detect cgroup capabilities
 - Issue stability warning on kernels <3.8
 - 'docker push' buffers on disk instead of memory
 - Fix 'docker diff' for removed files
 - Fix 'docker stop' for ghost containers
 - Fix handling of pidfile
 - Various bugfixes and stability improvements

## 0.1.7 (2013-04-18)
 - Container ports are available on localhost
 - 'docker ps' shows allocated TCP ports
 - Contributors can run 'make hack' to start a continuous integration VM
 - Streamline ubuntu packaging & uploading
 - Various bugfixes and stability improvements

## 0.1.6 (2013-04-17)
 - Record the author an image with 'docker commit -author'

## 0.1.5 (2013-04-17)
 - Disable standalone mode
 - Use a custom DNS resolver with 'docker -d -dns'
 - Detect ghost containers
 - Improve diagnosis of missing system capabilities
 - Allow disabling memory limits at compile time
 - Add debian packaging
 - Documentation: installing on Arch Linux
 - Documentation: running Redis on docker
 - Fixed lxc 0.9 compatibility
 - Automatically load aufs module
 - Various bugfixes and stability improvements

## 0.1.4 (2013-04-09)
 - Full support for TTY emulation
 - Detach from a TTY session with the escape sequence `C-p C-q`
 - Various bugfixes and stability improvements
 - Minor UI improvements
 - Automatically create our own bridge interface 'docker0'

## 0.1.3 (2013-04-04)
 - Choose TCP frontend port with '-p :PORT'
 - Layer format is versioned
 - Major reliability improvements to the process manager
 - Various bugfixes and stability improvements

## 0.1.2 (2013-04-03)
 - Set container hostname with 'docker run -h'
 - Selective attach at run with 'docker run -a [stdin[,stdout[,stderr]]]'
 - Various bugfixes and stability improvements
 - UI polish
 - Progress bar on push/pull
 - Use XZ compression by default
 - Make IP allocator lazy

## 0.1.1 (2013-03-31)
 - Display shorthand IDs for convenience
 - Stabilize process management
 - Layers can include a commit message
 - Simplified 'docker attach'
 - Fixed support for re-attaching
 - Various bugfixes and stability improvements
 - Auto-download at run
 - Auto-login on push
 - Beefed up documentation

## 0.1.0 (2013-03-23)
 - First release
 - Implement registry in order to push/pull images
 - TCP port allocation
 - Fix termcaps on Linux
 - Add documentation
 - Add Vagrant support with Vagrantfile
 - Add unit tests
 - Add repository/tags to ease image management
 - Improve the layer implementation

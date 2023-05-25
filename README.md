# Shitlist

Things that have made my shitlist and why.

## Helm

- Templating data structures
- Templating semantic whitespace
- Sprig? Why do we need _another_ templating language?
- Inheritance
- Lousy to no composition patterns
- Impossible to debug once you start flow-controlling bits on and off
- PITA to test
- Abuses k8s configMaps/secrets to store state
- Hits the configMap size limit if you parameterize secrets like certificates
- Unique chart registry format - was OCI or the other 500, proven repository formats not enough?
- Used to need Tiller deployed to cluster
- Misleading - makes you think you can write generalized charts but they're a mistake

## Dotnet

- Microsoft.
- XML
- Awful CI and build tooling.
- /XML
- Compiled but still has a runtime.
- Basic stuff that's solved-for like version bumping and git hook management just... aren't solved with it (despite it's age). It took v7.0 to even introduce a string literal or container awareness.
- Simple stuff like passing credentials for authenticating to package repositories or services are just painful.
- Project definition files aren't readily handleable by humans.
- NuGet packaging was also overly permissive and has been abused like people packaging jQuery, or earlier versions of NuGet so they can run deprecated functions.

## Python

Easy to write, awful to ship, a nightmare to consume.

- It will break in unexpected ways without typing
- Typing isn't even enforcable at run-time, it's purely a static check.
- Original `requirements.txt` was SORELY limited and is still in-use and beloved (⁉)
- There's loads of project/packaging/environment tools out there but only like 2 are actually good all-round and people shit on you for using anything.
- Container-wise the symlinking and system packages just fuck you over.
- Nothing's isolated so install like 3 things and it's already dependency hell everywhere.
- Python's release cadence outstrips plenty of packages so you get trapped there
- You wanna ship anything you gotta either do janky compiling or send the entire runtime.
- `setup.py` runs arbitrary code and a huge portion of packages on PyPi a) don't have dependency metadata, so you have run it to work out what they need and/or b) don't have compiled wheels, so you gotta waste compute making them.
- Slow.
- The Python/Pip/PipX bootstrapping issue.
- Wasted effort with competing projects like conda vs anaconda vs mamba.
- It's the de-facto language of DevOps so I'm tied to it.
- Nothing's git-aware so if you actually want to test using a package in place you gotta publish versions that _may_ work.
- Some of it's `TOML`, other stuff like `pre-commit` is `YAML`, yet other stuff like `requirements.txt` is still `ini`
- Pip packaging was far too permissive so people have done shit like packaging an entire Julia application + runtime inside it, or whole data sets. So rolling back that support will piss off plenty of people.
- Parallel installations of Python are a pain to manage. If you do it via something like the system package manager you risk messing up your system, but if you do it out-of-band other stuff can mess with your installation too.

## Nix

Love it, but like it's the problem child.

- Nix/NixOS/NixPkgs confusion
- Basically none of the documentation is ever _quite_ up-to-date cos - changes. So you gotta go spelunking.
- NixLang - seriously? Like there wasn't something appropriate for this already?
- NixLang performance is poor. There's some work under way to RIIR but I don't think it's official and may have stalled.
- Some of the post-install patch steps are hella-janky
- Wrapping other tools with overlap can be tricky (see: Python)

## Dockerfiles/Containerfiles

I love containers and do plenty of my workflow using them.

- Brittle.
- Imperative.
- Not very hermetic.
- Pain to do simple stuff like make arguments mandatory.
- Pain to do anything with secrets, only recently did we get a better solution than multi-stage builds.
- Doesn't let you _actually_ pin a manifest digest without 3rd party tooling like `docker-lock`
- Allowing unqualified images and falling back to whatever's configured at the daemon.
- Docker was only available rootful daemon for far too long. Both `buildah` and `podman` proved that the daemon wasn't required.
- Docker desktop adds like no value unless you feel the need to click things. At least it's affordable...

## GitLab

I quite like GitLab but it's got gotchas, Jack.

- Immediate effect of any project changes to all branches. E.g. change in CI variables, settings.
- No clear audit trail or history of project changes.
- No way to expose project settings read-only to users so they can troubleshoot.
- No option to phase-out CI variables with a warning.
- No option to schedule CI variable changes (e.g. rotating credentials)
- Is trying _very_ hard to do everything but in doing a handful of specific features that _I_ want aren't getting worked on.

## Homebrew

- Slow: Ruby
- Interpreted: to even look at anything you need the entire Ruby runtime
- Fat: I have no idea how they did it but every install with Homebrew just seems huge. I think they've done full dependency separation but without deduplication, so you wind up with like 50 versions of the same `libc`.
- Tragic: Mac deserved better than this.
- Slow and chatty: until v4 it was interacting with `git` directly to deal with package metadata. Now I believe it just downloads a JSON blob with all the listings.

## HCL

- Semantic newlines but not spaces (mostly)
- Should have just been a functional language but won't admit it
- Not favorable compared to other options (Cue, Dhall, Sprig, Nix, Jinja2... the list goes on)


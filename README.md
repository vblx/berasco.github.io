# berasco.github.io
static weblog www.berasco.de 

### dev corner ###
This info is *not* needed unless you want to do everything again from
scratch!  I.e. if you want to make another blog / landing page for
another customer, you will have to repeat these steps below.  This is
the most simple incarnation of a Static blog / landingpage website
generated by [Hugo](https://gohugo.io/) hosted on [GitHub
Pages](https://pages.github.com/) using [GitHub
Actions](https://github.com/features/actions) for automatic Build &
Deploy.

#### Dev Laptop needs the following prerequisites: ####
- Have [Git](https://git-scm.com/downloads)
  [installed](https://github.com/git-guides/install-git)
  - Windows users can use ["git bash"](https://gitforwindows.org/)
  - MacOS users can use [homebrew](https://brew.sh/) `brew install git`
  - Linux users probably already have git installed.
- Optional steps for work with GitHub (note: git and github are 2
  completely different things!)
  - Optional: if you prefer a GUI client for git instead of using the
  Terminal you can install [GitHub
  Desktop](https://github.com/apps/desktop)
  - Also optional: install [gh-cli](https://cli.github.com) if you
  prefer to work on the Terminal.
- Have the [Go](https://go.dev) programming language
  [installed](https://go.dev/doc/install), or use
  '[goenv](https://github.com/go-nv/goenv)' to install a version of your
  choice (highly recommended).
- Have [Hugo](https://gohugo.io/) installed:
``` sh
  CGO_ENABLED=1 go install -tags extended github.com/gohugoio/hugo@latest
  goenv rehash #if using goenv. or just restart your shell/terminal
```

#### how everything was setup initially ####
- create a new [github](https://github.com) account and chose a username
- create a new public repo named something like 'MYGITHUBUSER.github.io'
  - example: if your GitHub username is 'asdfmyuser', the name of the
    new repo would be _exactly_ "asdfmyuser.github.io".
- on GitHub, in the repo's settings tab, under "pages" choose "deploy
from a branch" and as branch chose "gh-pages" (click save!).
- clone repo locally: `gh repo clone <repo>` (or use GitHub Desktop).
- generate new hugo site:
``` sh
  hugo new site --force MYNEWREPO #replace MYNEWREPO with actual folder!

```
- add and configure elate theme from ./hugo.toml:
``` sh
  cd MYNEWREPO #replace MYNEWREPO with actual folder!
  git submodule add https://github.com/saey55/hugo-elate-theme themes/hugo-elate-theme
  cp themes/hugo-elate-theme/exampleSite/config.toml ./hugo.toml
  $EDITOR ./hugo.toml #make changes for new site
```
- add github action in `./.github/workflows/gh-pages.yaml`
- push everything:
``` sh
  git commit -am'push recent changes' && git push
```

Contributing
------------


### Commit Message Format

We have very precise rules over how our git commit messages can be formatted.  This leads to **more
readable messages** that are easy to follow when looking through the **project history**.  But also,
we use the git commit messages to **generate change log**.

The commit message formatting can be added using a typical git workflow or through the use of a CLI
wizard ([Commitizen](https://github.com/commitizen/cz-cli)). To use the wizard, run `yarn run commit`
in your terminal after staging your changes in git.


#### Conventional Commits 1.0.0-beta.2

Each commit message consists of a **header**, a **body** and a **footer**.  The header has a special
format that includes a **type**, a **scope** and a **subject**:

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

The **header** is mandatory and the **scope** of the header is optional.

Any line of the commit message cannot be longer 100 characters! This allows the message to be easier
to read on GitHub as well as in various git tools.

The footer should contain a [closing reference to an issue](https://help.github.com/articles/closing-issues-via-commit-messages/) if any.

See https://www.conventionalcommits.org for more details.

>###### Summary
>
>As an open-source maintainer, squash feature branches onto `master` and write
>a standardized commit message while doing so.
>
>The commit message should be structured as follows:
>
>---
>
>```
><type>[optional scope]: <description>
>
>[optional body]
>
>[optional footer]
>```
>---
>
><br />
>The commit contains the following structural elements, to communicate intent to the
>consumers of your library:
>
>1. **fix:** a commit of the _type_ `fix` patches a bug in your codebase (this correlates with [`PATCH`](http://semver.org/#summary) in semantic versioning).
>1. **feat:** a commit of the _type_ `feat` introduces a new feature to the codebase (this correlates
>  with [`MINOR`](http://semver.org/#summary) in semantic versioning).
>1. **BREAKING CHANGE:** a commit that has the text `BREAKING CHANGE:` at the beginning of its optional body or footer section introduces a breaking API change (correlating with [`MAJOR`](http://semver.org/#summary) in semantic versioning). A breaking change can be
>  part of commits of any _type_. e.g., a `fix:`, `feat:` & `chore:` types would all be valid, in addition to any other _type_.
>1. Others: commit _types_ other than `fix:` and `feat:` are allowed, for example [commitlint-config-conventional](https://github.com/marionebl/commitlint/tree/master/%40commitlint/config-conventional) (based on the [the Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)) recommends `chore:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, and others. We also recommend `improvement` for commits that improve a current implementation without adding a new feature or fixing a bug. Notice these types are not mandated by the conventional commits specification, and have no implicit effect in semantic versioning (unless they include a BREAKING CHANGE, which is NOT recommended).
><br />
>A scope may be provided to a commit's type, to provide additional contextual information and
>is contained within parenthesis, e.g., `feat(parser): add ability to parse arrays`.
>
>###### Specification
>
>The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).
>
>1. Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, etc.,
>   followed by a colon and a space.
>1. The type `feat` MUST be used when a commit adds a new feature to your application
>  or library.
>1. The type `fix` MUST be used when a commit represents a bug fix for your application.
>1. An optional scope MAY be provided after a type. A scope is a phrase describing
>  a section of the codebase enclosed in parenthesis, e.g., `fix(parser):`
>1. A description MUST immediately follow the type/scope prefix.
>  The description is a short description of the code changes, e.g.,
>  _fix: array parsing issue when multiple spaces were contained in string._
>1. A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
>1. A footer MAY be provided one blank line after the body (or after the description if body is missing).
>  The footer SHOULD contain additional issue references about the code changes (such as the issues it fixes, e.g.,`Fixes #13`).
>1. Breaking changes MUST be indicated at the very beginning of the footer or body section of a commit. A breaking change MUST consist of the uppercase text `BREAKING CHANGE`, followed by a colon and a space.
>1. A description MUST be provided after the `BREAKING CHANGE: `, describing what
>  has changed about the API, e.g., _BREAKING CHANGE: environment variables now take precedence over config files._
>1. The footer MUST only contain `BREAKING CHANGE`, external links, issue references, and other meta-information.
>1. Types other than `feat` and `fix` MAY be used in your commit messages.


#### Spec ext.

###### Revert

If the commit reverts a previous commit, it should begin with `revert: `, followed by the header of the reverted commit. In the body it should say: `This reverts commit <hash>.`, where the hash is the SHA of the commit being reverted.

###### Type

Must be one of the following:

* **revert**: Revert a previous commit
* **feat**: A new feature
* **fix**: A bug fix
* **build**: Changes that affect the build system or external dependencies (example scopes: webpack, yarn)
* **ci**: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
* **docs**: Documentation only changes
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
* **test**: Adding missing tests or correcting existing tests
* **chore**: Changes to the build process or auxiliary tools and libraries such as documentation generation

###### Scope

The scope should be the name of the yarn package affected (as perceived by the person reading the changelog generated from commit messages.

There are currently a few exceptions to the "use package name" rule:

* **github**
* **changelog**: used for updating the release notes in CHANGELOG.md
* **package**: used for changes that change the yarn package layout in all of our packages, e.g. public path changes, package.json changes done to all packages, d.ts file/format changes, changes to bundles, etc.
* none/empty string: useful for `style`, `test` and `refactor` changes that are done across all packages (e.g. `style: add missing semicolons`)

###### Subject

The subject contains a succinct description of the change:

* use the imperative, present tense: "change" not "changed" nor "changes"
* don't capitalize the first letter
* no dot (.) at the end

###### Body

Just as in the **subject**, use the imperative, present tense: "change" not "changed" nor "changes".
The body should include the motivation for the change and contrast this with previous behavior.

###### Footer

The footer should contain any information about **Breaking Changes** and is also the place to
reference GitHub issues that this commit **Closes**.

**Breaking Changes** should start with the word `BREAKING CHANGE:` with a space or two newlines. The rest of the commit message is then used for this.

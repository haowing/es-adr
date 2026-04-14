# Energy Systems Architectural Decision Records (Markdown)

## Quick start

* [`adr-template.md`](template/adr-template.md) has all sections, with explanations about them.
* [`adr-template-minimal.md`](template/adr-template-minimal.md) only contains mandatory sections, with explanations about them. <!-- ### Consequences also contained, though marked as "optional" -->
* [`adr-template-bare.md`](template/adr-template-bare.md) has all sections, which are empty (no explanations).
* [`adr-template-bare-minimal.md`](template/adr-template-bare-minimal.md) has the mandatory sections, without explanations. <!-- ### Consequences also contained, though marked as "optional" -->

Copy it into `docs/decisions`.
For each ADR, copy the template to `nnnn-title.md` and adapt.
Longer explanation: Head to <https://adr.github.io/madr/#applying-madr-to-your-project>.

## ES ADR Naming Convention
We follow the same naming convention as defined in [Energy Systems Internal Service Documents ] (https://dnv.sharepoint.com/teams/Energy-Systems-Internal-Service-Documents/SitePages/Energy-Systems-Internal-Service-Documents.aspx).

For example: ADR-***SERVICE AREA***-***ARCHITECTURE DOMAIN***-***NUMBER/CODE***-TITLE 

```markdown
e.g. ADR-DIG-AI-001-The-LLM-Use-In-Energy-Systems.md
```

## Development hints

* ES ADR follows [Semantic Versioning 2.0.0](https://semver.org/) and documents changes in a `CHANGELOG.md` following [keep a changelog 1.0.0](http://keepachangelog.com/en/1.0.0/).
* Issues can be reported at <https://github.com/haowing/es-adr/issues>.
* ES ADR uses [markdownlint](https://github.com/DavidAnson/markdownlint) as Linter for Markdown files. Use [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) for checking for linting issues in VS Code.
* `template/adr-template.md` is mirrored to `docs/decisions/adr-template`.
  However, following YAML front matter is added to make it handled properly by the [Just the Docs Jekyll Template](https://just-the-docs.github.io/just-the-docs/).

  ```markdown
  ---
  parent: Decisions
  nav_order: 100
  title: ADR Template
  ---
  ```

## License and Disclaimer

This work is extended from <https://adr.github.io/madr/>. It is dual-licensed under [MIT](https://opensource.org/licenses/MIT) and [CC0](https://creativecommons.org/share-your-work/public-domain/cc0/).

Please also refer to its scientific work below:

```bibtex
@InProceedings{Kopp2018,
  author    = {Kopp, Oliver and Armbruster, Anita and Zimmermann, Olaf},
  booktitle = {ZEUS},
  title     = {Markdown Architectural Decision Records: Format and Tool Support},
  year      = {2018},
}
```

```yaml
SPDX-License-Identifier: MIT OR CC0-1.0
```

## How to start Jekyll locally

For rendering the `docs` directory, Jekyll is needed.

For local development, follow the [Jekyll installation instructions](https://jekyllrb.com/docs/installation/).
Installing the latest version of ruby followed by `gem install bundler` should be enough.

Afterwards, run

```terminal
bundle install
jekyll serve --livereload
```

and go to <http://localhost:4000/madr/> in your browser.

## Updating just-the-docs

* Adapt `docs/Gemfile` to use newer just-the-docs version. Thereby check <https://github.com/just-the-docs/just-the-docs-template/blob/main/Gemfile> for versions.
* Delete `docs/Gemfile.lock`. Start `bundle install`.
* Check <https://github.com/just-the-docs/just-the-docs/blob/main/CHANGELOG.md>.
* Check <https://just-the-docs.com/migration/>.

## Execution

### Option 1 (with Docker)

'''
cd "C:\Users\HAODIN\OneDrive - DNV\Projects\DNV\es-adr\docs"
docker build -t es-adr-docs .
docker run --rm -p 4000:4000 -v "${PWD}:/srv/jekyll" es-adr-docs
'''

### Option 2 (with Ruby installed)

cd "C:\Users\HAODIN\OneDrive - DNV\Projects\DNV\es-adr\docs"
gem install bundler
bundle install
bundle exec jekyll serve --livereload

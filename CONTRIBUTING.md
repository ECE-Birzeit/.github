# Contributing to ECE Lab Manuals

These manuals are read by students at the bench, in the middle of a lab session. A wrong pin number or a step that no longer matches the IDE costs a whole group their time, so every fix helps, however small.

This guide covers every repository in [ECE-Birzeit](https://github.com/ECE-Birzeit).

## Ways to help

- **Report a problem.** Open an issue on the lab's repository (see the table below). Include the page link, what is wrong, and what you expected. For setup problems, add your OS and the tool version.
- **Fix it yourself.** Every manual page has an **Edit this page on GitHub** link at the bottom. GitHub forks the repository for you and opens a pull request with your change.
- **Propose something bigger,** like a new experiment or a reworked section. Open an issue first so we can agree on the approach before you write it.
- **Add a lab.** Teaching a lab that should be here? [Get in touch](https://mabushelbaia.com).

## Repositories

| Repository | What it is | Stack |
|:--|:--|:--|
| [encs4110](https://github.com/ECE-Birzeit/encs4110) | ENCS4110 Computer Design Laboratory site | VitePress |
| [encs4110-manual](https://github.com/ECE-Birzeit/encs4110-manual) | LaTeX source of the ENCS4110 PDF manual | LaTeX |
| [encs4101](https://github.com/ECE-Birzeit/encs4101) | ENCS4101 Embedded Systems Laboratory site | VitePress |
| [encs5150](https://github.com/ECE-Birzeit/encs5150) | ENCS5150 Advanced Computer Systems Engineering Laboratory site | VitePress |
| [landing-page](https://github.com/ECE-Birzeit/landing-page) | [birzeit.me](https://birzeit.me), the list of all labs | Static HTML |

## Running a site locally

The lab sites need [Node.js](https://nodejs.org) 24 and npm.

```sh
git clone https://github.com/ECE-Birzeit/encs4101.git
cd encs4101
npm ci
npm run dev        # http://localhost:5173, reloads as you edit
```

Differences per repository:

- **encs4110** keeps the site in `docs/` and pulls the PDFs in as a submodule. Clone with `--recurse-submodules` and use `npm run docs:dev` / `npm run docs:build`.
- **encs4110-manual** needs a TeX distribution with `pdflatex` and Inkscape. Build with `make`.
- **landing-page** is a single `index.html`. Open it in a browser.

Each repository's README has the details.

## Writing guidelines

- **Write for someone at the bench.** One action per step, in the imperative: "Set PA5 as GPIO output", not "PA5 should be set as an output".
- **Follow the existing pages.** Experiments share a structure (objectives, pre-lab, background, procedure). Copy it rather than inventing a new one.
- **Code must run.** Test every snippet on the lab's board or toolchain. Long files go in `snippets/` and are included into the page instead of pasted.
- **Images** go in `public/images/exp<N>/` with kebab-case names. Compress screenshots and give every image alt text that says what it shows.
- **Callouts:** use `::: tip` for hints, `::: warning` for anything that can damage hardware or lose work, and `::: danger` sparingly.
- **Links:** link to other pages with root-relative paths (`/setup`, `/experiments/2`). The build fails on dead links, which is intended.

## Pull requests

1. Branch from `main` and keep each pull request to one topic.
2. Run the build before you push (`npm run build`, or `npm run docs:build` in encs4110). It catches dead links and broken includes.
3. Say what changed and why. Add a screenshot for anything visual.
4. Write commit messages as a short imperative summary, like `Fix ADC channel in experiment 4`.

Once merged into `main`, a change is live within a couple of minutes.

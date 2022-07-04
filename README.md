# Development

Clone the repo and its submodules (themes)

```bash
$ git clone --recurse-submodules https://github.com/dearalgorithm/joji_fx
```

Start the Development server

```bash
$ cd joji_fx
$ hugo server -D
```

# Deployment

The deployment is done by Github Actions, check out [./github/workflows/cd.yml](.github/workflows/cd.yml) (in this repo) if you would like to know which jobs & steps are done.

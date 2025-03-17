## About

This GitHub Action sets up the [packwiz CLI](https://github.com/packwiz/packwiz) utility in your workflow. It allows you to install the packwiz CLI either from the latest release or from a specific commit hash. This action is useful if you want to automate generating and publishing your modpack directly in your CI.

---

> [!NOTE]
> Currently this action will install and compile packwiz from source
> everytime it runs. We may cache this in the future but at the moment
> we don't really see a need to as the compilation is fairly fast and 
> doesn't add much time to CI runs but this can definitely be improved.

---
* [Usage](#usage)
* [Customizing](#customizing)
  * [inputs](#inputs)

## Usage

```yaml
name: Example Workflow

on: [ push ]

jobs:
  list-mods:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code 
        uses: actions/checkout@v4

      - name: Setup packwiz CLI
        uses: vspr-sh/packwiz-setup-action@master

      - name: List mods
        run: packwiz list
```

## Customizing

### Inputs

The following inputs can be used as `step.with` keys:

| Name         | Type   | Default  | Description                                                                            |
|--------------|--------|----------|----------------------------------------------------------------------------------------|
| `go-version` | String | `>=1.19` | Version of Go to use                                                                   |
| `commit`     | String | `latest` | Specific commit hash from [packwiz/packwiz](https://github.com/packwiz/packwiz) to use |

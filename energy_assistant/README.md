# Energy Assistant

[![Build Status](https://github.com/pail23/energy-assistant-backend/workflows/Build/badge.svg)](https://github.com/pail23/energy-assistant-backend/actions?query=workflow%3ABuild)
[![Code Quality](https://goreportcard.com/badge/github.com/pail23/energy-assistant-backend)](https://goreportcard.com/report/github.com/pail23/energy-assistant-backend)
[![Open in Visual Studio Code](https://img.shields.io/static/v1?logo=visualstudiocode&label=&message=Open%20in%20VS%20Code&labelColor=2c2c32&color=007acc&logoColor=007acc)](https://open.vscode.dev/pail23/energy-assistant-backend)
[![OSS hosting by cloudsmith](https://img.shields.io/badge/OSS%20hosting%20by-cloudsmith-blue?logo=cloudsmith)](https://cloudsmith.io/~Energy Assistant/packages/)
[![Latest Version](https://img.shields.io/github/release/pail23/energy-assistant-backend.svg)](https://github.com/pail23/energy-assistant-backend/releases)
<!-- [![Pulls from Docker Hub](https://img.shields.io/docker/pulls/andig/Energy Assistant.svg)](https://hub.docker.com/r/andig/Energy Assistant) -->
<!-- [![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=48YVXXA7BDNC2) -->

Energy Assistant is an extensible EV Charge Controller with PV integration implemented in [Go][2]. Featured in [PV magazine](https://www.pv-magazine.de/2021/01/15/selbst-ist-der-groeoenlandhof-wallbox-ladesteuerung-selbst-gebaut/).

![Screenshot](../docs/4_Energy Assistant_tablet_standard_light.png)

## Features

- simple and clean user interface
- HomeAssistant [add-on](https://github.com/pail23/energy-assistant-addon)

## Getting Started

You'll find everything you need in our [documentation](https://docs.Energy Assistant.io/) (German).

## Contribute

To build Energy Assistant from source, [Go][2] 1.18 and [Node][3] 16 are required.

Build and run go backend. The UI becomes available at http://127.0.0.1:7070/

```sh
make
./Energy Assistant
```

For frontend development start the Vue toolchain in dev-mode. Open http://127.0.0.1:7071/ to get to the livelreloading development server. It pulls its data from port 7070 (see above).

```sh
npm install
npm run start
```

### Code formatting

We use linters (golangci-lint, Prettier) to keep a coherent source code formatting. It's recommended to use the format-on-save feature of your editor. For VSCode use the [Go](https://marketplace.visualstudio.com/items?itemName=golang.Go), [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) and [Veture](https://marketplace.visualstudio.com/items?itemName=octref.vetur) extension. You can manually reformat your code by running:

```sh
make lint
make lint-ui
```

### Changing UI code

To ensure reproducability the build frontend artifacts are part of the source code repository. If you've made changes to frontend code, please make sure to rebuild the production assets before you commit.

```sh
make ui
```

### Changing templates

Energy Assistant supports a massive amount of different devices. To keep our documentation and website in sync with the latest software the core project (this repo) generates meta-data that's pushed to the `docs` and `Energy Assistant.io` repository. Make sure to update this meta-data every time you make changes to a templates.

```sh
make docs
```

If you miss one of the above steps Gitub Actions will likely trigger a **Porcelain** error.

## Sponsorship

Energy Assistant believes in open source software. We're committed to provide best in class EV charging experience.
Maintaining Energy Assistant consumes time and effort. With the vast amount of different devices to support, we depend on community and vendor support to keep Energy Assistant alive.

While Energy Assistant is open source, we would also like to encourage vendors to provide open source hardware devices, public documentation and support open source projects like ours that provide additional value to otherwised closed hardware. Where this is not the case, Energy Assistant requires "sponsor token" to finance ongoing development and support of Energy Assistant.

The personal sponsor token requires a [Github Sponsorship](https://github.com/sponsors/andig) and can be requested at [cloud.Energy Assistant.io](https://cloud.Energy Assistant.io/). A sponsor token is valid for one year and can be renewed any time with active sponsorship.

## Background

Energy Assistant is heavily inspired by [OpenWB][1]. However, in 2019, I found OpenWB's architecture slightly intimidating with everything basically global state and heavily relying on shell scripting. On the other side, especially the scripting aspect is one that contributes to OpenWB's flexibility.

Hence, for a simplified and stricter implementation of an EV charge controller, the design goals for Energy Assistant were:

- typed language with ability for systematic testing - achieved by using [Go][2]
- structured configuration - supports YAML-based [config file](Energy Assistant.dist.yaml)
- avoidance of feature bloat, simple and clean UI - utilizes [Vue.js][4] and [Bootstrap][5]
- containerized operation beyond Raspberry Pi - provide multi-arch [Docker Image][6]

[1]: https://github.com/snaptec/openWB
[2]: https://golang.org
[3]: https://nodejs.org/
[4]: https://vuejs.org
[5]: https://getbootstrap.org
[6]: https://hub.docker.com/r/andig/Energy Assistant

# Craft CMS DDEV Starter

Craft CMS DDEV Starter is a modern development template for Craft CMS projects. It leverages DDEV for robust local hosting and Vite for efficient front-end bundling. With integrated support for Tailwind CSS, Alpine.js, and essential plugins, this starter project streamlines your workflow from development to deployment.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Configuration](#configuration)
- [Installation](#installation)
- [Local Development](#local-development)
- [Makefile Commands](#makefile-commands)
- [Plugins and Libraries](#plugins-and-libraries)
- [Contributing](#contributing)
- [License](#license)

## Overview

This starter project is designed to give you a fast and flexible setup for Craft CMS development. With DDEV managing your local environment and Vite optimizing your front-end build process, you can focus on creating and scaling your project without worrying about configuration overhead.

## Features

- **Local Development:** Powered by [DDEV](https://ddev.readthedocs.io/)
- **Front-end Bundling & HMR:** Utilizes [Vite 5.x](https://vitejs.dev/)
- **Utility-first CSS:** Built with [Tailwind CSS 3.x](https://tailwindcss.com)
- **Lightweight Reactivity:** Uses [Alpine.js 3.x](https://alpinejs.dev/)
- **Hosting Ready:** Configured for deployment on [Servd](https://servd.host/)
- **Unified CLI:** Simplified commands via a [Makefile](https://www.gnu.org/software/make/manual/make.html)

## Prerequisites

Before you begin, ensure you have the following installed on your local machine:

1. [Docker](https://www.docker.com/)
2. [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) (Windows only)
2. [DDEV](https://ddev.readthedocs.io/) (minimum version 1.19)
3. (Optional but recommended) [Composer](https://getcomposer.org/)

## Getting Started

Clone the repository to your desired directory:

```shell
git clone https://github.com/Gyurkin/craftcms-ddev.git YOUR_PROJECT_PATH
```

> **Note:** Replace \`YOUR_PROJECT_PATH\` with a new or empty directory.

Next, remove the existing Git history:

```shell
cd YOUR_PROJECT_PATH
rm -rf .git
```

Set up your environment with the default configuration files:

```shell
cp .env.example .env
mv composer.json.default composer.json
mv .gitignore.default .gitignore
rm README.md
```

## Configuration

If you wish to customize your DDEV setup (for example, changing the default domain from \`https://craftcms.ddev.site\`):

```shell
ddev config
```

Follow the prompts:
- **Project Name:** For example, entering \`mysite\` will create the URL \`https://mysite.ddev.site\`
- **Docroot Location:** Defaults to \`web\` (recommended)
- **Project Type:** Defaults to \`craftcms\` (recommended)

## Installation

To install a fresh copy of Craft CMS and set up your environment, run:

```shell
make install
```

This command will:

1. Copy your local SSH keys into the container (useful for [craft-scripts](https://github.com/nystudio107/craft-scripts/))
2. Start your DDEV project
3. Install Composer and npm dependencies
4. Perform an initial build with Vite
5. Generate and save \`APP_ID\` and \`SECURITY_KEY\` in your \`.env\` file
6. Launch the Craft CMS installer to set up your admin credentials and install plugins

After installation, open your project in your default browser with:

```shell
ddev launch
```

### Troubleshooting

When you run the `ddev launch` command, you might encounter an error indicating an exit status 127. 
This typically means that the system cannot find a required command—in most cases, `xdg-open`.

On Debian/Ubuntu-based systems, you can install it by running:

```shell
sudo apt-get install xdg-utils
```

## Local Development

For an enhanced development experience with hot module replacement (HMR) via Vite, run:

```shell
make dev
```

This command will:

1. Copy local SSH keys into the container (as configured for craft-scripts)
2. Start the DDEV project and install necessary dependencies (Composer and npm)
3. Execute a one-time Vite build
4. Launch the Vite development server

Then, simply visit your project domain in a browser to verify that everything is working as expected.

## Makefile Commands

A Makefile is included to provide a unified CLI for common tasks:

- **\`make install\`**: Set up the project and install Craft CMS.
- **\`make up\`**: Start the DDEV project with SSH keys and dependency checks.
- **\`make dev\`**: Build front-end assets and run the Vite development server.
- **\`make build\`**: Build all front-end assets for production.
- **\`make pull\`**: Pull remote database and assets (requires [craft-scripts](https://github.com/nystudio107/craft-scripts/)).

### Makefile on Windows

Running `Makefile` CLI tasks on Windows may result in errors if the required utilities aren’t installed by default. Windows doesn’t come with a native Unix-like environment, so tasks that work on Linux or macOS might fail until you set up the proper tools.

#### Install a Make Utility

If you have [Chocolatey](https://chocolatey.org/) installed, you can quickly install GNU Make by running:

```shell
choco install make
```

#### Verify the Installation

- Open a Command Prompt, PowerShell, or your preferred terminal.
- Run the following command to check that Make is installed correctly:

```shell
make --version
```

## Plugins and Libraries

### Craft CMS Plugins

- [CKEditor](https://plugins.craftcms.com/ckeditor)
- [CP Field Inspect](https://plugins.craftcms.com/cp-field-inspect)
- [Servd Assets and Helpers](https://github.com/servdhost/craft-asset-storage)
- [Vite](https://github.com/nystudio107/craft-vite)
- [Seo](https://github.com/ethercreative/seo)
- [Minify](https://github.com/nystudio107/craft-minify)

### Tailwind CSS Plugins

- [Aspect Ratio](https://github.com/tailwindlabs/tailwindcss-aspect-ratio)
- [Line Clamp](https://github.com/tailwindlabs/tailwindcss-line-clamp)
- [Typography](https://github.com/tailwindlabs/tailwindcss-typography)

### JavaScript Libraries

- [Alpine.js](https://alpinejs.dev/)
- [Lazysizes](https://afarkas.github.io/lazysizes/)

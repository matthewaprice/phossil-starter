# phossil starter

A new site for [phossil](https://github.com/matthewaprice/phossil), the small PHP site kit with routing and typed components that builds to plain static HTML, ready for AWS Amplify or any static host.

You get routes, typed views and components while you build, and a folder of static files when you deploy.

**[Read the documentation at phossil.dev](https://phossil.dev)**

## Quick start

phossil runs PHP, nginx and Vite in Docker. You also need PHP and Node on your machine, for Composer and pnpm:

- Docker, with Compose
- PHP 8.5 with Composer
- Node 24 or later, with pnpm

```sh
composer create-project matthewaprice/phossil-starter my-site
cd my-site
pnpm install       # Vite, Tailwind, oxfmt and oxlint
docker compose up --build
```

`create-project` asks whether to start a git repository with a first commit. Answer `n` to skip it.

Open http://localhost:8000.

## What's here

- `app/` is your site: routes in `routes/web.php`, views, controllers, data, the `Layout` around every page, and the CSS, JS and images.
- `tests/` holds PHPUnit tests for the views and controllers.
- The routing, components and build come from the `matthewaprice/phossil` package in `vendor/`.
- `.claude/` holds an optional pull request skill for [Claude Code](https://claude.com/claude-code): run `/pull-request` on a branch to check it and write its PR description. Delete the folder if you don't use Claude Code.

## Build

With the containers still running, build the site and zip it:

```sh
composer build:zip
```

You get `dist/`, and `dist.zip` beside it, ready to upload to any static host.

## Test, format and lint

```sh
composer test      # PHPUnit, in the php container
pnpm format        # oxfmt: JS, CSS, JSON, Markdown
pnpm format:check  # the same, without writing
pnpm lint          # oxlint: app/js
```

## License

[MIT](LICENSE)

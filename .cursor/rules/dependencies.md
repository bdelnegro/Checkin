# Dependency rules

## Ruby (`Gemfile`)

- **Runtime**: Declare production and shared gems in the main groups; keep **SQLite** in `development`/`test` and **PostgreSQL** (`pg`) in `production` only, matching this template.
- **Versions**: Respect the locked Ruby version (`.ruby-version`) and prefer explicit gem versions or conservative ranges when adding gems.
- **Bundler**: Run `bundle install` after changing the Gemfile; commit `Gemfile.lock` when dependencies change.

## JavaScript (`package.json` / Yarn)

- **Webpacker**: Front-end dependencies live in `package.json`; use **Yarn** (this repo has `yarn.lock`).
- **Separation**: Do not move Rails-only concerns into npm packages unnecessarily; use gems for server-side behavior and npm for packs/build tooling.

## Cross-cutting

- Avoid duplicating the same behavior in Ruby and JS unless there is a clear boundary (e.g. validation UX vs. server-side validation).

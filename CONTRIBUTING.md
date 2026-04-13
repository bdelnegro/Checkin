# Contributing

## Package architecture

This repository is a **Rails 6** application with **Webpacker** for JavaScript packs and **Sprockets** for stylesheets. HTTP handling follows classic **MVC** under `app/`; **ActiveAdmin** resources live in `app/admin` and define admin screens (including list filters). JavaScript entry points are under `app/javascript/packs`; shared Ruby code outside the usual Rails paths may live in `lib/`, and extra models can be autoloaded from `vendor/app/models` as configured in `config/application.rb`.

For a fuller layout map, see [`.cursor/rules/architecture.md`](.cursor/rules/architecture.md).

## Dependency rules

- **Ruby**: Use `Gemfile` / Bundler; keep environment-specific gems aligned with the existing groups (e.g. `sqlite3` for dev/test, `pg` for production). Commit `Gemfile.lock` when dependencies change. Details: [`.cursor/rules/dependencies.md`](.cursor/rules/dependencies.md).
- **JavaScript**: Use **Yarn** and `package.json` for Webpacker-related packages; keep server behavior in Ruby unless the front end truly needs it.

## Adding a new filter (Active Admin)

Admin list filters are configured on each **ActiveAdmin** resource in `app/admin/*.rb` using `filter :attribute` (and optional options for input type or associations). See [`.cursor/rules/active-admin-filters.md`](.cursor/rules/active-admin-filters.md) and the example in `app/admin/admin_users.rb`.

**Note:** Rails [parameter filtering for logs](https://guides.rubyonrails.org/configuring.html#config-filter-parameters) is separate from Active Admin sidebar filters; see `config/initializers/filter_parameter_logging.rb`.

## Cursor rules index

| Topic | File |
|--------|------|
| App layout and layers | [`.cursor/rules/architecture.md`](.cursor/rules/architecture.md) |
| Ruby and JS dependencies | [`.cursor/rules/dependencies.md`](.cursor/rules/dependencies.md) |
| Active Admin filters | [`.cursor/rules/active-admin-filters.md`](.cursor/rules/active-admin-filters.md) |

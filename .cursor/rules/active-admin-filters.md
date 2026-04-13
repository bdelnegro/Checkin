# Active Admin filters

Filters apply to the **index** list for a registered resource. They are declared in the resource file under `app/admin/`.

## Add a filter

1. Open the resource file, e.g. `app/admin/<resource>.rb` (see `app/admin/admin_users.rb` for an example).
2. Inside `ActiveAdmin.register ...`, add a line such as:
   - `filter :attribute_name` — uses Ransack-compatible predicates on the model attribute.
   - For associations or custom behavior, use ActiveAdmin’s options (e.g. `filter :author, as: :select`).
3. Ensure the attribute exists on the model (or is a registered Ransack “ransacker” if you need something custom).
4. Reload the admin index page and confirm the sidebar filter appears and scopes results correctly.

## Conventions

- Prefer filters that map clearly to database columns or simple scopes; keep heavy logic in the model as a **scope** and expose it via Ransack if needed.
- Do not log or expose secrets: sensitive params are filtered in `config/initializers/filter_parameter_logging.rb` (Rails logs), separate from Active Admin UI filters.

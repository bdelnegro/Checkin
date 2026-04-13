# Application architecture

This app is a **Rails 6** API-ready web app with **Webpacker 4** for JavaScript packs and **Sprockets** for stylesheets and legacy assets.

## Layout

| Area | Role |
|------|------|
| `app/controllers`, `app/models`, `app/views` | Standard Rails MVC. |
| `app/admin` | ActiveAdmin resource definitions (index screens, filters, forms). |
| `app/javascript/packs` | Webpacker entry points; compiled via Webpack. |
| `app/assets` | Sprockets assets (CSS, images, ActiveAdmin JS hooks). |
| `config` | Routes, environments, initializers. |
| `lib` | Non-Rails code and rake tasks. |
| `spec` | RSpec tests. |
| `vendor/app/models` | Extra autoloaded models (see `config/application.rb`). |

Admin UI and authentication for staff use **Devise** with **`AdminUser`**, mounted under ActiveAdmin’s routes.

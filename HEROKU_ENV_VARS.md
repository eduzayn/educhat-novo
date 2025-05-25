# Heroku Environment Variables Configuration

## Required Environment Variables

Set these environment variables in your Heroku app dashboard or using heroku CLI:

```bash
# Rails Configuration
heroku config:set RAILS_ENV=production --app lit-oasis-44056
heroku config:set RACK_ENV=production --app lit-oasis-44056
heroku config:set SECRET_KEY_BASE=$(openssl rand -hex 64) --app lit-oasis-44056
heroku config:set FRONTEND_URL=https://lit-oasis-44056.herokuapp.com --app lit-oasis-44056

# Chatwoot Configuration
heroku config:set INSTALLATION_ENV=heroku --app lit-oasis-44056
heroku config:set REDIS_OPENSSL_VERIFY_MODE=none --app lit-oasis-44056

# Rails 7.1 Configuration
heroku config:set RAILS_SERVE_STATIC_FILES=true --app lit-oasis-44056
heroku config:set RAILS_LOG_TO_STDOUT=true --app lit-oasis-44056

# Mailer Configuration
heroku config:set MAILER_SENDER_EMAIL=support@lit-oasis-44056.herokuapp.com --app lit-oasis-44056
heroku config:set SMTP_DOMAIN=lit-oasis-44056.herokuapp.com --app lit-oasis-44056

# Security
heroku config:set FORCE_SSL=true --app lit-oasis-44056

# Storage
heroku config:set ACTIVE_STORAGE_SERVICE=local --app lit-oasis-44056

# Optional: Super Admin (generate a strong password)
heroku config:set CHATWOOT_SUPER_ADMIN_PASSWORD=YourStrongPassword123! --app lit-oasis-44056
```

## Database & Redis

These should be automatically configured by Heroku add-ons:
- DATABASE_URL (set by heroku-postgresql addon)
- REDIS_URL (set by heroku-redis addon)

## After Setting Environment Variables

1. Deploy again:
```bash
git add .
git commit -m "fix: simplified Procfile and added env vars documentation"
git push heroku main
```

2. Run database setup manually:
```bash
heroku run rails db:setup --app lit-oasis-44056
heroku run rails db:migrate --app lit-oasis-44056
heroku run rails db:seed --app lit-oasis-44056
``` 
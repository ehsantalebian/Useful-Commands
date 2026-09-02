# Ruby Commands

Here are some sets of Ruby commands that can assist you in your day-to-day activities.

- Start Puma Service
```bash
bundle exec puma -d
```

- Restart Puma Service
```bash
pumactl phased-restart
```

- Migrate
```bash
rails db:migrate
```

- Rails Console
```bash
rails c
```

- Start Sidekiq Service
```bash
bundle exec sidekiq -d -L log/sidekiq.log
```

- Start Crono Service
```bash
bundle exec crono start RAILS_ENV=production
```

- Start Delayed Job Service
```bash
RAILS_ENV=production bin/delayed_job -n 5 start
```

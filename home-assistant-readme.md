# Install Home-Assistant

## Fresh installation

1. Deploy the [home assistant compose file](./home-assistant.yml)
2. Open a terminal inside the home-assistant container
3. Paste the following command when you are in side the `/config` folder:
```bash
cat > configuration.yaml <<'EOF'

#Loads default set of integrations. Do not remove.
default_config:

# Load frontend themes from the themes folder
frontend:
  themes: !include_dir_merge_named themes

# Configuration for reverse proxy support (required for Coolify)
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 127.0.0.1
    - 10.0.0.0/8
    - 172.16.0.0/12
    - 192.168.0.0/16
  ip_ban_enabled: true
  login_attempts_threshold: 5

EOF
```
4. Restart the container

## With back up

1. Go to you existing installation and add at least this section to the `configuration.yml`:

```yml
http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 127.0.0.1
    - 10.0.0.0/8
    - 172.16.0.0/12
    - 192.168.0.0/16
```
2. create a backup of your home assistant instance
3. Follow the instructions from [fresh installation](#fresh-installation)
4. open the web interface and start the backup



# ReadMe

## What is Hatchet

[Hatchet](https://hatchet.run) is...

> a distributed, fault-tolerant task queue which replaces traditional message brokers and pub/sub systems - built to solve problems like concurrency, fairness, and durability.

## Using this repo

This repo is for deploying Hatchet via Docker Compose both locally during develompent and on a remote server in production.

## Local Development

In terminal, run...
`bash hatchet.dev.start.sh`

## Production

In terminal, run...
`bash hatchet.production.start.sh`

Your instance is now running at `http://localhost:8888`

The default credentials are:

```
Email: admin@example.com
Password: Admin123!!
```

You will want to change them immediately for production usage.

Before integrating into your code base, you will also need to generate an API key.

You can do this in the UI by visiting...

http://localhost:8888/tenant-settings/api-tokens

Or, in the terminal, run this command:

```
cat <<EOF > .env
HATCHET_CLIENT_TOKEN="$(docker compose run --no-deps setup-config /hatchet/hatchet-admin token create --config /hatchet/config --tenant-id 707d0855-80ab-4e1f-a156-f1c4546cbf52 | xargs)"
HATCHET_CLIENT_TLS_STRATEGY=none
EOF
```

## See Also

- [Hatchet Documentation](https://docs.hatchet.run)
- [Deploying Hatchet via Docker Compose](https://docs.hatchet.run/self-hosting/docker-compose)
- [Configuration Options](https://docs.hatchet.run/self-hosting/configuration-options)
- [Data Retention](https://docs.hatchet.run/self-hosting/data-retention)
- [Improving Performance](https://docs.hatchet.run/self-hosting/improving-performance)

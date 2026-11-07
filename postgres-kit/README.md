# postgres-kit

Release repository for the postgres-kit Docker Compose Kit.

## Package

- `postgres-kit.zip` — release archive. Contains exactly one root directory named `postgres-kit`.
- `postgres-kit.zip.sha256` — SHA-256 checksum for the archive.
- `LICENSE` — proprietary commercial license for the kit.

## How to install

### 1. Download

Download `postgres-kit.zip` and `postgres-kit.zip.sha256` from this repository.

### 2. Verify the checksum

Verify the archive integrity before extracting:

```bash
sha256sum -c postgres-kit.zip.sha256
```

Expected result:

```
postgres-kit.zip: OK
```

If the result is anything other than OK, do not extract or use the archive. Re-download
`postgres-kit.zip` and `postgres-kit.zip.sha256` from this repository.

### 3. Extract the kit

```bash
unzip postgres-kit.zip
cd postgres-kit
```

The extracted kit contains:

```text
postgres-kit/
├── compose.yaml        # Docker Compose service definitions
├── .env.example        # Example environment file (no real secrets)
├── config/
│   └── env-schema.yaml # Environment schema
├── data/               # Persistent data directories
├── docs/               # Documentation
├── scripts/
│   ├── env-management  # Environment manager binary
│   └── mdbook          # Documentation builder
├── README.md
├── CHANGELOG.md
└── LICENSE
```

### 4. Create the environment file

The real `.env` is intentionally not shipped. Create it from `.env.example`:

```bash
cp .env.example .env
```

Edit `.env` with your values. Never commit `.env`.

### 5. Validate the environment (optional)

Validate `.env` against the schema using the shipped `env-management` binary:

```bash
./scripts/env-management --kit . validate
```

### 6. Start the services

Run the kit under a Compose profile. Select your variant:

```bash
docker compose --profile <variant> up -d
```

### 7. Verify the service is running

```bash
docker compose --profile <variant> ps
```

## Documentation

Full documentation is shipped inside the ZIP under `docs/`:

- `docs/README.md` — kit overview, variants, quick start
- `docs/INSTALLATION.md` — installation and deployment
- `docs/SECURITY.md` — security considerations
- `docs/BACKUP.md` — backup procedures
- `docs/RESTORE.md` — restore procedures
- `docs/TROUBLESHOOTING.md` — troubleshooting guide

## Verification

SHA-256 checksum: see `postgres-kit.zip.sha256`.

Kit version: 1.0.0


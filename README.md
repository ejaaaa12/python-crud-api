# python-crud-api

REST API sederhana (Python) dengan pipeline CI/CD: GitHub -> Jenkins -> Docker.

## Endpoint

| Method | Path | Keterangan |
|---|---|---|
| GET | /health | Status layanan |
| GET | /messages | Daftar pesan |
| POST | /messages | Buat pesan (`{"message": "..."}`) |
| DELETE | /messages?index=N | Hapus pesan pada index N |

## Menjalankan manual

```bash
docker build -t python-crud-api:manual .
docker volume create production-api-data
docker run -d --name production-api-container -p 5000:5000 \
  -v production-api-data:/var/lib/backend_data python-crud-api:manual
curl -i http://localhost:5000/health
```

## Pipeline

Jenkinsfile: Checkout -> Syntax check -> Build image -> Deploy -> Health check.
Data disimpan di Docker named volume `production-api-data`.Webhook test 11/04/2026 17:46:43

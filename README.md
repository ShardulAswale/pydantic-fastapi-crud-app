# FastAPI Car CRUD API

Python API for storing car records in MongoDB, with Pydantic validation and HTTP Basic authentication.

## How it works

The `car_api` package separates routes, service operations, authentication and database setup. Motor performs asynchronous MongoDB operations, and a counter assigns IDs when omitted. Car fields include make, model, year, colour and price.

## Usage

Requires Python 3.13 or later and an accessible MongoDB instance. From the repository root, inside your Python environment:

```sh
python -m pip install -e ".[dev]"
python -m uvicorn car_api.main:app --reload
```

Configure `MONGODB_URI` and `MONGODB_DB` through environment variables or a local `.env` file. Defaults are `mongodb://localhost:27017` and `car_api`.

## Endpoints

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/healthz` | Health response. |
| POST, GET | `/cars` | Create or list cars. |
| GET, PUT, DELETE | `/cars/{car_id}` | Retrieve, replace or delete a car. |

Open `http://127.0.0.1:8000/swagger` for interactive documentation. Car routes use demo credentials `admin` / `changeme`. Listing accepts `limit` and `offset`.

## Notes

This checkout has no WebSocket, token or item routes. Use the editable package install above; the frozen requirements contain a reference to another repository. Tests require MongoDB and can modify its car collection.

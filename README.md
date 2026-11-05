# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in dollars. Zones are `local` and `regional`; weights must be positive.

| Service    | Local base | Regional base | Per-kg rate |
|------------|-----------|---------------|-------------|
| `standard` | $5.00     | $8.00         | $1.50       |
| `express`  | $12.00    | $15.00        | $1.50       |

Express adds a flat $7 surcharge over standard for either zone. Passing an
unknown service or zone raises `ValueError`.

The command-line entry point prints a quote for an order:

```
python -m warehouse.cli 2 local
python -m warehouse.cli 2 local --service express
```

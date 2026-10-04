# floww

> **Credit:** Originally published at [prakharpks02/floww-api-ver1](https://github.com/prakharpks02/floww-api-ver1).

This is a flat snapshot of the Django files from the Floww API prototype, related to prakharpks02/floww-api-ver1. `views.py` holds Django REST Framework API views for delivery/order operations. They check the request parameters and return placeholder data. Each call is logged through the `ErrorLogApi` and `UsageLogApi` models.

## API views (in `views.py`)

| View | Method | Input |
|---|---|---|
| `EditOrderInstructions` | POST | `orderId`, `instruction` |
| `GetOrderDetails` | GET | `orderId` query param |
| `Track_Order` | GET | `orderId` query param, returns status and timestamp |
| `Cancel_Orders` | POST | list of order IDs |
| `GetTaskDetails` | GET | `taskID` query param |
| `EstimateTaskCost` | POST | `vendorCode`, `orderList`, and other order fields |
| `RequestDeliveries` | POST | `vendorCode`, `productDescription`, `orderType`, `orderList`, `rentalPlan`, `serviceList` |

## Status

This is a prototype. All files sit flat in the repo root, but `manage.py` expects a `main_project` package and the views expect an `app1` app. The views are not routed in `urls.py`, and `models.py` references an undefined `CHAR_SIZE_MEDIUM` constant. Several views also pass log fields that the models do not define. You need to restructure the files into a standard Django project layout before it will run.

## Tech stack

Python, Django, Django REST Framework, SQLite (default).

## Running locally (after you restructure into `main_project/` + `app1/`)

```bash
pip install django djangorestframework
export DJANGO_SECRET_KEY="your-secret-key"
# optional: export DJANGO_DEBUG=1
python manage.py migrate
python manage.py runserver
```

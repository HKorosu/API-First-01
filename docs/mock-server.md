# Mock Server and UI Prototype

## Start the Prism Mock Server

From the project root, run:

```powershell
npx.cmd --yes @stoplight/prism-cli mock src\main\resources\shop-api.yaml --host 127.0.0.1 --port 4010
```

Prism serves the contract routes from `http://127.0.0.1:4010`. For example:

```powershell
curl.exe "http://127.0.0.1:4010/products?page=0&size=10&sort=price,desc"
```

The first `npx` run downloads Prism if it is not already cached. Stop the server with `Ctrl+C`.

## Open the UI Prototype

Start the Spring Boot app and open `http://localhost:8080/shop-prototype.html`.
If port 8080 is occupied, run the packaged application on another port:

```powershell
java -jar target\shop-api-0.0.1-SNAPSHOT.jar --server.port=18081
```

Then open `http://localhost:18081/shop-prototype.html`. The page defaults to the Prism URL above and demonstrates loading products, creating a customer, and placing an order using the spec examples.

## Test the Live API in Swagger UI

With Spring Boot running, open `http://localhost:8080/swagger-ui.html`
(or replace `8080` with the configured application port). Swagger UI loads the
original `shop-api.yaml` contract.

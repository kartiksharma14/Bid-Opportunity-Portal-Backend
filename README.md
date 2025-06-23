# Bid Opportunity Portal Backend

This project is a Spring Boot application that powers the Bid Opportunity Portal. It exposes a REST API for managing opportunities, user accounts, roles, permissions and other reference data. The codebase is built with Java 17 and Maven.

## Features

- **User Management** – CRUD operations for users with validation and hierarchical parent/child relationships.
- **Authentication & Authorization** – JWT based login, refresh token workflow and token blacklisting. API requests are filtered by `SecurityFilter` using roles and permissions defined in `PermissionConfig`.
- **Role & Permission Management** – Endpoints to manage roles (`RoleController`) and permissions (`PermissionsController`). Roles are linked to permissions using `RolesPermission` entities.
- **Business Domain** – Controllers and services for business units, deals, segments, plans and approval workflows. 
- **Scraped Data API** – `/api/scrape` endpoints accept tender data from an external scraper and store it with quarterly and fiscal year calculations.
- **RBAC** – Fine‑grained permission checks to restrict endpoints per user role.

## Project Structure

```
src/main/java/com/portal/bid
 ├── config          # Spring configuration (security, CORS, permissions)
 ├── controller      # REST controllers
 ├── entity          # JPA entities
 ├── repository      # Spring Data repositories
 ├── service         # Service interfaces
 ├── service/implementation
 │   └── ...         # Concrete service implementations
 ├── filter          # JWT and API key filters
 ├── security        # CustomUserDetails for Spring Security
 └── util            # Utility classes (e.g., JWTUtil)
```

`BidApplication.java` contains the main method and bootstraps Spring Boot.
Configuration values such as database connection and secret keys are defined in `src/main/resources/application.properties`.

## Building and Running

Ensure Java 17 and Maven are installed. Compile and run the application with:

```bash
mvn clean install
mvn spring-boot:run
```

The APIs will start on port 8080 by default. Refer to the controller classes under `src/main/java/com/portal/bid/controller` for available endpoints.

## Testing

No unit tests are included. Running `mvn test` will simply build the project. You may add tests under `src/test/java`.

## License

This code is provided as-is with no specific license.

# IT Service Desk Management

Capstone implementation based on the IT Service Desk Management specification.

## Solution structure

- `Capstone.DAL` - Data Access Layer using Entity Framework Core and SQLite.
- `Capstone.API` - Web API service layer with authentication, authorization, validation and structured exception handling.
- `Capstone.React` - React presentation layer.

## Database

The SQLite database is stored at:

`Capstone.DAL/Database/ServiceDeskDB.db`

The API runs migrations on startup and seeds the required master/user data.

## Users and authentication

The application supports any number of database-backed users. Users are not hard-coded into the login screen. The Admin can create new User accounts from **Manage Users**; each new account is stored in SQLite and can immediately log in.

Passwords are stored as salted PBKDF2 hashes. Passwords are never returned by the API.

### Demo accounts

| Role | Username | Password |
|---|---|---|
| Admin | `admin` | `admin@123` |
| User | `employee` | `employee@123` |
| User | `rahul` | `rahul@123` |
| User | `kathryn` | `kathryn@123` |
| User | `john` | `john@123` |
| User | `priya` | `priya@123` |
| User | `alex` | `alex@123` |
| User | `sarthak` | `qwerty123` |

Each request is stored in SQLite with the authenticated user's username in `RaisedBy`. The Admin dashboard retrieves all requests, while a User dashboard retrieves only requests belonging to the signed-in user.

### Admin user management

Log in as `admin`, open **Manage Users**, enter a username and an 8-20 character password, and select **Create User**. New users are stored in the `Users` table as User-role accounts.

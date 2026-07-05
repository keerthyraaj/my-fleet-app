# Fleet management app guide

This project now has a simple authentication flow and a fleet dashboard.

## What changed

### 1. Backend login flow
The backend accepts a login request from the frontend and checks the user in PostgreSQL.

It uses:
- Express to create the web server
- `pg` to talk to PostgreSQL
- `bcrypt` to verify the password hash
- `dotenv` to load the database connection string from the `.env` file

### 2. Dashboard data endpoint
A new endpoint was added at `/api/dashboard/stats`.

It reads the logged-in user's email, finds the matching user, then returns:
- total number of assigned fleets
- total distance covered
- average battery life
- active, charging, and maintenance fleet counts
- fleet type breakdown

### 3. Frontend dashboard UI
After a successful login, the React app loads a dashboard screen instead of only showing a welcome message.

The dashboard includes:
- summary cards for fleet count, distance, and battery
- a chart-like bar view for fleet types
- progress bars for operational statuses

## Database tables used
The dashboard depends on the PostgreSQL tables from the DDL file in the backend folder.

The important tables are:
- `users` — stores login details and names
- `fleets` — stores fleet information such as vehicle type, battery, distance, and status
- `user_fleets` — links users to the fleets they are assigned to

## How the flow works
1. User enters email and password in the React form.
2. React sends the values to the backend login endpoint.
3. The backend checks the email in the `users` table.
4. If the password is valid, the backend returns the user’s name and email.
5. React uses the email to request dashboard statistics from the backend.
6. The backend joins the `users`, `fleets`, and `user_fleets` tables and sends the results to the UI.

## Important notes for beginners
- Never store plain-text passwords in the database.
- Always keep the `.env` file private.
- The dashboard only works if your database contains matching rows in the `users`, `fleets`, and `user_fleets` tables.

## How to run the app

### Backend
```bash
cd backend
npm start
```

### Frontend
Open the frontend folder in a browser using a simple static server, or use your preferred local dev setup.

## Next steps
You can improve this later by adding:
- real charts with Chart.js or Recharts
- a sidebar navigation menu
- fleet detail pages
- filters by status or vehicle type

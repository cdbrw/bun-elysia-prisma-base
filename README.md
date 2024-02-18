[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/ospb5B?referralCode=codebrew)

# Bun with Elysia & Prisma
This is a template repo for the base of a Bun server using Elysia for the API and Prisma as the ORM for a Postgres DB.

You can [deploy on Railway](https://railway.app/template/ospb5B?referralCode=codebrew) or simply [create a new repo](https://github.com/thecodebrew/bun-elysia-prisma-base/generate) using this template.

## Development
Start a Docker container for the Postgres database
```
docker run --name dev-postgres -p 5432:5432 -e POSTGRES_PASSWORD=12345678 -d postgres
```

Add the `DATABASE_URL` env variable to a _.env_ file
```
DATABASE_URL="postgresql://postgres:12345678@localhost:5432/postgres?schema=public"
```

To start the development server run:
```bash
bun run dev
```
Open http://localhost:3000/ with your browser to see the result.

## Production
1. Ensure the `DATABASE_URL` env variable is set to `${{Postgres.DATABASE_URL}}`
2. Set custom build command to `bunx prisma migrate deploy` in order to run database migrations
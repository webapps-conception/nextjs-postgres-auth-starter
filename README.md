<p align="center">
  <a href="https://nextjs-postgres-auth.vercel.app/">
    <img src="/public/logo.png" height="96">
    <h3 align="center">Next.js Prisma PostgreSQL Auth Starter</h3>
  </a>
</p>

<p align="center">
This is a <a href="https://nextjs.org/">Next.js</a> starter kit that uses <a href="https://next-auth.js.org/">Next-Auth</a> for simple email + password login<br/>
<a href="https://www.prisma.io/">Prisma</a> as the ORM, and a <a href="https://vercel.com/postgres">Vercel Postgres</a> database to persist the data.</p>

<br/>

## Deploy Your Own

You can clone & deploy it to Vercel with one click:

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?demo-title=Next.js%20Prisma%20PostgreSQL%20Auth%20Starter&demo-description=Simple%20Next.js%2013%20starter%20kit%20that%20uses%20Next-Auth%20for%20auth%20and%20Prisma%20PostgreSQL%20as%20a%20database.&demo-url=https%3A%2F%2Fnextjs-postgres-auth.vercel.app%2F&demo-image=%2F%2Fimages.ctfassets.net%2Fe5382hct74si%2F7rsVQ1ZBSiWe9JGO6FUeZZ%2F210cba91036ca912b2770e0bd5d6cc5d%2Fthumbnail.png&project-name=Next.js%%20Prisma%20PostgreSQL%20Auth%20Starter&repository-name=nextjs-postgres-auth-starter&repository-url=https%3A%2F%2Fgithub.com%2Fvercel%2Fnextjs-postgres-auth-starter&from=templates&skippable-integrations=1&env=NEXTAUTH_SECRET&envDescription=Generate%20a%20random%20secret%3A&envLink=https://generate-secret.vercel.app/&stores=%5B%7B"type"%3A"postgres"%7D%5D)

## Developing Locally

You can clone & create this repo with the following command

```bash
npx create-next-app nextjs-typescript-starter --example "https://github.com/vercel/nextjs-postgres-auth-starter"
```

## Getting Started

Configurer le fichier .env.local:
```bash
cp .env.example .env.local
```

Sur le tableau de bord Vercel, recopier les variables d'environnement du projet ``nextjs-postgres-auth-starter``.

First, run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

L'utilisateur et le mot de passe de connexion est identique à celui de production.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Prisma CLI Installation

```bash
yarn add prisma --save-dev
```

- [Prisma CLI reference](https://www.prisma.io/docs/reference/api-reference/command-reference)

## Accès psql
### Docker

Démarrer un client psql sous docker:
```bash
docker pull postgres:latest
docker run -it --rm --hostname pg postgres:latest bash
```

### Connexion en psql
Sur le tableau de bord Vercel sous Storage et **nextjs-postgres-auth-st-postgres**, recopier la commande psql:

```bash
psql "postgres://default:XXXX@xxx.eu-central-1.postgres.vercel-storage.com:5432/verceldb"

verceldb=> select * from public."User";
 id |             email             |                           password                           
----+-------------------------------+--------------------------------------------------------------
  1 | contact@webapps-conception.fr | XXXX
(1 row)

verceldb=> \d "User"
                              Table "public.User"
  Column  |  Type   | Collation | Nullable |              Default               
----------+---------+-----------+----------+------------------------------------
 id       | integer |           | not null | nextval('"User_id_seq"'::regclass)
 email    | text    |           | not null | 
 password | text    |           | not null | 
Indexes:
    "User_pkey" PRIMARY KEY, btree (id)
    "User_email_key" UNIQUE, btree (email)

verceldb=> \q
```

### Export de la base de données

```bash
pg_dump "postgres://default:XXXX@xxx.eu-central-1.postgres.vercel-storage.com:5432/verceldb" > nextjs-typescript-starter.dump
```

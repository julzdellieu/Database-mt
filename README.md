<<<<<<< HEAD
# Database-mt
Built with Node, Prisma, Postgres, JWT auth, Docker, and tenant-aware RBAC baked in.

One backend app serves many tenants, all isolated by tenantId but sharing the same code and infrastructure.
Uses a shared database by default, with every query scoped to the tenant from verified JWTs (no client trust).


A multitenant web application designed to securely serve multiple tenants from a single codebase while keeping data isolated and configurable per tenant.
Multitenancy means one app, many tenants. Each tenant:

Has isolated data

Can have its own users, roles, and settings

Shares the same infrastructure and deployment

This app supports tenant-aware authentication, authorization, and data access.

Architecture Overview

Backend: API-driven (Node.js / Express or similar)

Database: PostgreSQL

ORM: Prisma

Auth: JWT-based authentication with tenant context

Deployment: Docker-ready

Tenant Isolation Strategy

One of the following (depending on configuration):

Shared database, tenant_id per table (most common)

Separate schema per tenant

Separate database per tenant (enterprise use)

This repo uses shared DB + tenant_id by default.

Features

Tenant-aware authentication

Role-based access control (RBAC)

Secure data isolation per tenant

Prisma-powered database access

Environment-based configuration

Docker support

Ready for SaaS billing integration

Folder Structure backend/ │── prisma/ │ ├── schema.prisma │ └── migrations/ │── src/ │ ├── auth/ │ ├── tenants/ │ ├── users/ │ ├── middleware/ │ ├── routes/ │ └── server.ts │── .env.example │── docker-compose.yml │── package.json Environment Variables

Create a .env file based on .env.example.

** Getting Started

Install Dependencies npm install
Start PostgreSQL
Using Docker:

docker-compose up -d

Or use a local PostgreSQL instance.

Run Migrations npx prisma migrate dev
Start the Server npm run dev
Server runs at:

http://localhost:3000 Authentication Flow

User logs in

JWT is issued containing:

userId

tenantId

role

Middleware extracts tenant context

Prisma queries are automatically scoped to the tenant

This prevents cross-tenant data access by default.

Security Notes

All tenant-scoped queries must include tenantId

Never trust client-supplied tenant identifiers

Tenant context should come from verified JWTs only

Secrets must stay in environment variables

Common Use Cases

SaaS platforms

Internal tools for multiple companies

White-labeled applications

B2B dashboards

Roadmap Ideas

Tenant-level feature flags

Usage-based billing

Admin dashboard for tenant management

Audit logging per tenant

Rate limiting per tenant

License

MIT License

Disclaimer

This project is a foundation. Multitenancy introduces real security risks if implemented incorrectly.
=======
<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/dm/@nestjs/common.svg" alt="NPM Downloads" /></a>
<a href="https://circleci.com/gh/nestjs/nest" target="_blank"><img src="https://img.shields.io/circleci/build/github/nestjs/nest/master" alt="CircleCI" /></a>
<a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
<a href="https://opencollective.com/nest#backer" target="_blank"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor" target="_blank"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec" target="_blank"><img src="https://img.shields.io/badge/Donate-PayPal-ff3f59.svg" alt="Donate us"/></a>
    <a href="https://opencollective.com/nest#sponsor"  target="_blank"><img src="https://img.shields.io/badge/Support%20us-Open%20Collective-41B883.svg" alt="Support us"></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow" alt="Follow us on Twitter"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Project setup

```bash
$ npm install
```

## Compile and run the project

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Run tests

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

## Deployment

When you're ready to deploy your NestJS application to production, there are some key steps you can take to ensure it runs as efficiently as possible. Check out the [deployment documentation](https://docs.nestjs.com/deployment) for more information.

If you are looking for a cloud-based platform to deploy your NestJS application, check out [Mau](https://mau.nestjs.com), our official platform for deploying NestJS applications on AWS. Mau makes deployment straightforward and fast, requiring just a few simple steps:

```bash
$ npm install -g @nestjs/mau
$ mau deploy
```

With Mau, you can deploy your application in just a few clicks, allowing you to focus on building features rather than managing infrastructure.

## Resources

Check out a few resources that may come in handy when working with NestJS:

- Visit the [NestJS Documentation](https://docs.nestjs.com) to learn more about the framework.
- For questions and support, please visit our [Discord channel](https://discord.gg/G7Qnnhy).
- To dive deeper and get more hands-on experience, check out our official video [courses](https://courses.nestjs.com/).
- Deploy your application to AWS with the help of [NestJS Mau](https://mau.nestjs.com) in just a few clicks.
- Visualize your application graph and interact with the NestJS application in real-time using [NestJS Devtools](https://devtools.nestjs.com).
- Need help with your project (part-time to full-time)? Check out our official [enterprise support](https://enterprise.nestjs.com).
- To stay in the loop and get updates, follow us on [X](https://x.com/nestframework) and [LinkedIn](https://linkedin.com/company/nestjs).
- Looking for a job, or have a job to offer? Check out our official [Jobs board](https://jobs.nestjs.com).

## Support

Nest is an MIT-licensed open source project. It can grow thanks to the sponsors and support by the amazing backers. If you'd like to join them, please [read more here](https://docs.nestjs.com/support).

## Stay in touch

- Author - [Kamil Myśliwiec](https://twitter.com/kammysliwiec)
- Website - [https://nestjs.com](https://nestjs.com/)
- Twitter - [@nestframework](https://twitter.com/nestframework)

## License

Nest is [MIT licensed](https://github.com/nestjs/nest/blob/master/LICENSE).
>>>>>>> 49763c54 (Initial commit: add backend code and Prisma schema)

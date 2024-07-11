# One of my best real life projects that I am finishing right now

# Tammwe

This document provides an overview of the Tammwe project, a monorepo managed using [Yarn Workspaces](https://classic.yarnpkg.com/en/docs/workspaces/) and [Turborepo](https://turbo.build/repo). This monorepo contains a collection of shared libraries and applications, contributing to the Tammwe organization's ecosystem.

## Packages

- **[@tammwe/adinkra-ui](./packages/adinkra-ui/README.md)** - A collection of React UI components.
- **[@tammwe/database](./packages/database/README.md)** - Database module.
- **[@tammwe/eslint-config](./packages/eslint-config/README.md)** - ESLint configurations for different types of projects.
- **[@tammwe/tailwind-config](./packages/tailwind-config/README.md)** - Shared Tailwind CSS configuration.
- **[@tammwe/typescript-config](./packages/typescript-config/README.md)** - TypeScript configurations for different types of projects.
- **[@tammwe/utils](./packages/utils/README.md)** - A collection of utility functions.

## Applications

- **[docs](./apps/docs/README.md)** - Documentation/Storybook app for `@tammwe/adinkra-ui`.
- **[blog](./apps/blog/README.md)** - The Tammwe blog.
- **[frontpage](./apps/frontpage/README.md)** - The Tammwe frontpage.
- **[marketplace](./apps/marketplace/README.md)** - Marketplace platform.

## Deployment

Applications are deployed to [Vercel](https://vercel.com/). Deployment is managed via a bash script located at `/scripts/ignore-build-step.sh`, which determines whether to run the build (and thus the deploy) step. This script evaluates changes in the app folders between commits to decide on deployment. Changes in the `@tammwe/database` or `@tammwe/utils` packages trigger deployments for all apps due to their integration across the codebase.

Deployments occur only on the `main` branch, with the `marketplace` app also deployed on the `staging` branch. Preview deployments have been disabled, requiring local testing for pull requests.

## Development

### Prerequisites

Create a `.env` file in the root directory and each app directory based on the `.env.example` files, ensuring all required environment variables are set. For instance, `DATABASE_URL` is essential for database connections.

### Installation

To install dependencies, run:
```
yarn install
```

### Running the Apps
To start all apps on different ports, use:
```
yarn dev
```
To start a specific app, use:
```
yarn dev:app-name
```

### Testing
Each package and app has its own test setup. To run all unit tests, use:
```
yarn test
```
Unit tests are written using Vitest, ensuring that all Next.js server actions are thoroughly tested.

Please note that the source code and repository for Tammwe are not shared publicly, as per company policy. This README serves as an explanation of the project structure and functionalities.

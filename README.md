# InternMatch AI

InternMatch AI is a student internship-matching web application built with Next.js, React, and TypeScript. It helps students explore internships, maintain a profile, track applications, record achievements, and view skill/match-related guidance. It also includes an admin area for managing internship listings and shortlisting candidates.

> **Demo note:** The current project uses sample data and browser `localStorage` for much of its interactive demo state. This means data is stored in the browser and is not shared between users or devices. It is not a production authentication/database setup.

## Features

- Student landing page and dashboard
- Browse and explore internship listings
- Internship details and application tracking
- Student profile, skills, projects, and certifications
- Saved internships and match-related pages
- Achievements and learning roadmap
- Resume-related page
- Chatbot page
- Admin login/dashboard pages
- Admin internship management and candidate shortlist pages
- Health-check API endpoint at `/api/health`

## Technology stack

- Next.js 16
- React 19
- TypeScript
- Tailwind CSS 4
- Lucide React icons
- ESLint
- Drizzle ORM and PostgreSQL packages are included in the project dependencies, but the current demo store primarily uses browser local storage.

## Requirements

Install these first:

- Node.js (use a current LTS release)
- npm (included with Node.js)
- Visual Studio Code (recommended)

## Run locally in VS Code

1. Extract the ZIP file.
2. Open the extracted project folder in VS Code.
3. Open **Terminal → New Terminal**.
4. Confirm that the terminal is in the folder containing `package.json`.
5. Install dependencies:

   ```bash
   npm install
   ```

6. Start the development server:

   ```bash
   npm run dev
   ```

7. Open the local address shown in the terminal, usually:

   http://localhost:3000

Keep the terminal running while using the website. Press `Ctrl + C` to stop the server.

## Other commands

Check TypeScript:

```bash
npm run typecheck
```

Run ESLint:

```bash
npm run lint
```

Create a production build:

```bash
npm run build
```

Run the production build locally after building:

```bash
npm run start
```

## Database and environment configuration

The demo UI is designed to run with sample data and browser storage, so you can try the basic website without setting up a database **provided no database-backed route/module is invoked**.

The repository also contains PostgreSQL/Drizzle dependencies and a database connection module at `src/db/index.ts`. That module requires a `DATABASE_URL` environment variable. If you extend the project to use database-backed features, configure a PostgreSQL database and create a `.env.local` file in the project root, for example:

```env
DATABASE_URL=postgresql://USERNAME:PASSWORD@HOST:5432/DATABASE_NAME
```

Replace the example values with your actual database credentials. Do not commit real credentials to GitHub. The included Drizzle schema is currently only a placeholder, so database tables and persistent multi-user storage still need to be designed and configured before production use.

## Demo data and storage

- Sample internship listings and candidate information are defined in `src/lib/data.ts`.
- Demo application state is managed in `src/lib/demo-store.tsx`.
- Browser state is stored under the key `internmatch-ai-demo-v1`.
- Clearing the browser's site data may remove saved demo changes.
- Demo sign-in and role selection should not be treated as secure production authentication.

## Deployment

You can deploy the Next.js app to a platform that supports Next.js, such as Vercel:

1. Push the project to a Git repository.
2. Import the repository into your hosting provider.
3. Use `npm install` as the install command.
4. Use `npm run build` as the build command.
5. Use `npm run start` as the start command if your host requires it; many Next.js platforms configure this automatically.
6. Add `DATABASE_URL` only if you have configured and are using the PostgreSQL-backed parts of the project.
7. Deploy and open the URL provided by the host.

Before using this as a real service, add secure authentication, server-side authorization, database persistence, input validation, privacy controls, and production error handling. Do not rely on client-side demo role selection to protect admin pages.

## Project structure

```text
src/
  app/                 Next.js routes/pages and API routes
  components/          Shared UI and page components
  db/                  Drizzle/PostgreSQL connection and schema
  lib/
    data.ts            Sample internships, profiles, and achievements
    demo-store.tsx     Client-side demo state and localStorage
```

## Troubleshooting

- **`npm` is not recognized:** Install Node.js LTS, restart VS Code, and reopen the terminal.
- **`package.json` not found:** Use `cd` to move into the extracted project directory.
- **Port 3000 is busy:** Next.js may offer another port, such as 3001. Open the address printed in the terminal.
- **Dependency or lockfile issue:** Run `npm install` from the project root.
- **`DATABASE_URL is required`:** A database-backed module is being loaded. Configure `DATABASE_URL` in `.env.local` and ensure the PostgreSQL database is reachable, or keep the demo flow separate from database-backed code.

## License

No license file was included in the supplied project. Add a license before distributing or reusing the project publicly.

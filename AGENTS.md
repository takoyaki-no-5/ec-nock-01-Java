# AGENTS.md

## Cursor Cloud specific instructions

### Repository state (important)
This repo (`EC1000本ノック #001`) is **planning-stage only**. It currently tracks
just documentation and design artifacts — there is **no application source code**,
no build files (no `build.gradle`/`settings.gradle`/Gradle wrapper), no dependency
manifest, and no migrations:
- `README.md` — project plan / spec (Japanese)
- `docs/schema.dbml` — planned PostgreSQL schema (DBML)
- `docs/ERD.png` — ER diagram
- `.vscode/settings.json` — DBML ERD previewer theme

Because no app exists yet, there is nothing to `gradle build`/`gradle bootRun`, no
lint config, and no automated tests to run. Do not expect a runnable Spring Boot
service until source code is added.

### Intended stack (per README, for when code lands)
- Backend: Java 21 + Spring Boot (Spring MVC, jOOQ, Flyway, Bean Validation, Spring AOP, Spring Actuator, Lombok), built with Gradle.
- Frontend: server-rendered Thymeleaf + HTML/CSS/JS + Tailwind CSS.
- DB: PostgreSQL. PaaS: Render.

When source is added, prefer the project's Gradle **wrapper** (`./gradlew`) so the
Gradle version matches the project; do not rely on a system-wide `gradle`. Java 21
(`javac`/`java`) and Node 22 (`node`/`npm`, for Tailwind) are preinstalled.

### Local PostgreSQL (preinstalled system dependency)
PostgreSQL 16 is installed system-wide (not via the update script). It does **not**
auto-start; start the cluster before using the DB:
```
sudo pg_ctlcluster 16 main start   # check with: pg_lsclusters
```
A dev database is provisioned: db `ecdb`, role `ecuser` / password `ecpass` on
`localhost:5432`. Connect with `PGPASSWORD=ecpass psql -h localhost -U ecuser -d ecdb`.

### Verifying the environment without app code
The only concrete executable artifact is the DB schema. To sanity-check the env,
materialize `docs/schema.dbml` as SQL into `ecdb` and exercise the core e-commerce
flow (register user → list product → place order). This was validated during setup.

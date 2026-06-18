# Backend + MySQL Integration TODO

## Phase A — Restructure without behavior change

- [ ] Create folder structure under `server/`: config, controllers, routes, models, services, middleware, utils
- [ ] Introduce `.env` loading in server bootstrap
- [ ] Move existing auth middleware (`authenticateToken`, `requireRole`) into `server/middleware/*`
- [ ] Add centralized error handling middleware

## Phase B — MySQL DB layer

- [ ] Install `mysql` dependency (package.json update)
- [ ] Create `server/config/mysql.ts` using `mysql.createConnection()`
- [ ] Implement connection testing at startup + auto reconnect on disconnect
- [ ] Create `server/services/mysqlDb.ts` with parameterized query helpers

## Phase C — `/install` route

- [x] Implement `GET /install` route (kept existing `POST /install` too)
- [ ] Create MySQL tables with `CREATE TABLE IF NOT EXISTS` + indexes + foreign keys

- [ ] Seed default roles and admin/instructor/student users
- [ ] Seed demo courses/modules/lessons/quizzes/questions (enough for frontend dashboards)
- [ ] Return installation report JSON including created tables list

## Phase D — CRUD + endpoint integration

- [ ] Implement controllers/routes matching current `server.ts` paths
- [ ] Implement JWT auth + bcrypt password hashing
- [ ] Implement RBAC using roleId: 1 admin, 2 instructor, 3 student
- [ ] Ensure responses match existing frontend expectations

## Phase E — Verification

- [ ] Manual E2E: `/install` → login as seeded users → CRUD for courses/lessons/quizzes
- [ ] Verify no route mismatches, no SQL errors, no console errors

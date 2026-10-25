# Changelog

- `.gitignore` — excluded build outputs, local databases, key rings, and environment secrets.
- `.dockerignore` — excluded build outputs, backups, videos, local data, and secrets from Docker context.
- `AdmissionWeb.csproj` — added Npgsql for PostgreSQL persistence.
- `ButwalAdmission.sln` — updated the project reference for the flat repository layout.
- `Data/AdmissionStore.cs` — added provider selection, PostgreSQL schema compatibility, case-insensitive admin bootstrap, bounded pooling, and cross-provider inserts.
- `Data/DatabaseXmlRepository.cs` — added PostgreSQL-backed ASP.NET Data Protection key storage.
- `Data/schema.sql` — documented the SQLite Data Protection key table for local initialization.
- `DEPLOY_GUIDE.md` — added GitHub, Neon, Render, and restart-verification instructions.
- `Dockerfile` — added multi-stage .NET 10 container publishing, non-root runtime, and port 10000 configuration.
- `Program.cs` — added PostgreSQL/key-storage startup, admin bootstrap, CSRF validation, response compression, security headers, cache policy, and 404 fallback.
- `README.md` — updated root-layout build and production database instructions.
- `REVIEW_AND_REPAIR.md` — recorded audit findings, repairs, and verification limits.
- `wwwroot/admin.css` — formatted and restyled the admin dashboard with tokens, focus states, and mobile table scrolling.
- `wwwroot/assets/esewa-qr.jpg` — removed the older duplicate QR asset.
- `wwwroot/assets/esewa-qr.png` — added the supplied eSewa QR image without image processing.
- `wwwroot/favicon.svg` — added a favicon that embeds the unchanged logo asset.
- `wwwroot/index.html` — added QR payment guidance, QR dialog, conditional payment-step QR, and Open Graph metadata.
- `wwwroot/site.css` — formatted and extended the public design system with responsive sizing, glow, reduced-motion, and QR dialog styles.
- `wwwroot/site.js` — added QR dialog controls, conditional QR panel, scroll reveals, and mobile-menu state handling.
- `docs/screenshots/README.md` — documented the unavailable browser/screenshot checks.

`wwwroot/assets/butwal-skills-logo.png` was verified by SHA-256 and left byte-for-byte unchanged.

## Glow update (glass and glow theme, Dockerfile fix)

- Dockerfile: removed `groupadd/useradd app` (the official .NET image already has an `app` user, which caused `group 'app' already exists`, exit code 9). Now uses the built-in `$APP_UID` user. App still listens on port 10000.
- wwwroot/glow.css (new): dark-blue glass theme layered on top of site.css/admin.css. Glowing logo (white plate, pulsing glow, orbiting colour halo), glowing gradient pill buttons, frosted glass cards with a rotating glow border, glowing form focus, glowing QR tile, drifting light blobs in the background.
- wwwroot/index.html and admin.html: load glow.css after the existing stylesheets; theme-color updated.
- Layout bug fixes found during testing: (1) 4px sideways scroll on phones caused by grid columns that could not shrink; (2) "Start yourapplication." heading on phones (hidden line break); (3) "Sign out" button visible while logged out ([hidden] overridden by .button); (4) "(optional)" hints pushed inputs out of line in the form.
- Not changed: Program.cs, Data/*, Models/*, AdmissionWeb.csproj, the logo file (byte-for-byte identical), all JavaScript.


# LocalCloud redesign — change summary

Status: NOT built or type-checked (sandbox had no network, so `yarn install` was impossible).
Only a syntax-level TypeScript parse check was run. Run these before deploying:

    yarn install && yarn tsc && yarn lint && yarn build:production

## New files (resources/scripts)
- assets/localcloud.css                      shell/layout/card/badge/progress styles (tokens live in GlobalStylesheet)
- components/localcloud/LocalCloudLayout.tsx sidebar + header + content shell (drawer under 1024px)
- components/localcloud/LocalCloudSidebar.tsx, LocalCloudNav.tsx, LocalCloudHeader.tsx, LocalCloudLogo.tsx
- components/localcloud/LocalCloudCard.tsx, LocalCloudBadge.tsx, LocalCloudProgress.tsx

## Modified
- tailwind.config.js                 inverted gray scale -> light theme, soft-blue primary, 14-20px radii, hard ink shadows
- assets/css/GlobalStylesheet.ts     CSS variables (design tokens), focus-visible ring, reduced-motion
- routers/DashboardRouter.tsx, routers/ServerRouter.tsx   use LocalCloudLayout; server links moved to sidebar (same routes + permission gating)
- components/dashboard/DashboardContainer.tsx   hero, stat cards, server grid (real API data)
- components/dashboard/ServerRow.tsx            card with live CPU/memory/disk meters (same polling as before)
- elements/button/style.module.css, Input.tsx, Modal.tsx, ContentBox.tsx, GreyRowBox.tsx, SubNavigation.tsx, PageContentBlock.tsx
- server/console/style.module.css, Console.tsx  navy terminal, ink border, hard shadow (WebSocket code untouched)
- auth/LoginFormContainer.tsx        LocalCloud logo/tagline
- resources/views/templates/wrapper.blade.php, config/app.php   default app name / theme colors

## Untouched on purpose
API layer, state, WebSocket handlers, auth/session, window.PterodactylUser contract, PHP backend, DB.

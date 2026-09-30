# Taskara product map

Taskara is a back-office application for cleaning and facility-service companies. The canonical app origin is `https://taskara.de`.

## Signed-in routes

| Area | Route | Typical work |
| --- | --- | --- |
| Overview | `/app/dashboard` | Daily operational overview |
| Assistant | `/app/assistant` | Ask about business data and request supported creations |
| Customers | `/app/customers` | Customer master data and contacts |
| Objects | `/app/objects` | Buildings, sites, contracts, and object details |
| Employees | `/app/employees` | Team members and roles |
| Schedule | `/app/schedule` | One-off and recurring jobs, assignments, and conflicts |
| Tasks | `/app/tasks` | Internal tasks, priorities, due dates, and assignments |
| Time tracking | `/app/time-tracking` | Staff time entries |
| Absences | `/app/absences` | Leave and absence records |
| Field reports | `/app/field-reports` | Operational reports from the field |
| Articles | `/app/artikel` | Service and article catalog |
| Inbox | `/app/inbox` | Document upload and AI-assisted extraction |
| Quotes | `/app/quotes` | Quote drafts and delivery |
| Invoices | `/app/invoices` | Invoice drafts, delivery, and XRechnung export |
| Settings | `/app/settings` | Organization, account, subscription, security, and export |

## Product facts

- Taskara supports customers, contacts, objects, articles, employees, schedules, tasks, time tracking, field reports, quotes, invoices, and XRechnung exports.
- The Inbox accepts PDFs, scans, photos, and spreadsheets. AI extraction is available on eligible plans; uncertain fields should be reviewed rather than guessed.
- Roles include Inhaber, Admin, Büro, Manager, and Mitarbeiter. Only owners may grant owner rights or perform owner-only destructive actions.
- Free is intended for one organization without a team or AI document analysis. Starter includes up to five employees and AI analysis. Pro includes unlimited employees, prioritized support, and early feature access. Check `https://taskara.de/preise` for current pricing and terms instead of relying on memorized prices.
- Subscription and payment management is under Einstellungen → Konto → Abo verwalten. Data export is under Einstellungen → Konto → Datenexport.
- Documentation is at `https://taskara.de/hilfe`; support is at `https://taskara.de/support` or `mail@taskara.de`.

## Supported assistant creations

Taskara's in-app assistant can propose creation of schedule entries, internal tasks, customers, objects, quote drafts, and invoice drafts. The signed-in browser executes approved operations under Taskara's normal permissions. Treat visible Taskara records and validation messages as authoritative.

## Direct MCP tools

The Taskara MCP server at `https://taskara.de/api/mcp` uses Taskara OAuth and exposes:

- `list_organizations`
- `list_customers`
- `list_objects`
- `list_employees`
- `list_articles`
- `list_tasks`
- `list_schedule`
- `get_organization_settings`
- `update_organization_preferences`
- `create_task`
- `create_schedule_entry`
- `list_invoices`
- `get_owner_overview`
- `create_invoice_draft`
- `assign_schedule_employees`

Use these tools before browser control. Taskara membership and role checks still apply to every call. Follow nextCursor on list tools until null. Invoice creation supports confirmed catalog-based drafts only, with retry protection; it neither sends invoices nor claims tracked hours. Assignment supports unpublished one-off drafts only. Use the browser for publishing, recurring assignment changes, actual-time billing, sending, quotes and other unsupported workflows.

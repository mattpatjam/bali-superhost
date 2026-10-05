# Bali Superhost (BSH / BeStay / Kozystay)

Matthieu Jammers, Director of Business Development. Department: Real Estate Brokerage and Property Acquisition. Started 5 October 2026.

## Scope of this repo

Running the job: brokerage strategy, hiring, training, systems, and client work.

This repo deliberately contains no personal records. Compensation, ESOP, the employment negotiation, side businesses, and personal finances live in a separate private repo that is never cloned onto company hardware. Do not recreate any of that here.

## Structure

| Folder | Purpose |
|---|---|
| `Strategy/` | Brokerage build strategy, 90 day roadmap, positioning, go to market |
| `Hiring/` | Job descriptions and hiring criteria for the core team |
| `Training/` | Sales training program |
| `Systems/` | CRM and brokerage website requirements |
| `clients/` | Per client working documents (created by skills as needed) |
| `context/` | Role, team, and targets |
| `tracker.md` | Session log, active follow ups, file index |

## Skills and knowledge

Not in this repo. They come from `claude-toolkit`, symlinked at `~/.claude/` on each machine. Setup is in that repo's CLAUDE.md.

Skills that produce documents write to `clients/[client]/` relative to this workspace root.

## Tracker rule

After any session that modifies files here, update `tracker.md` before ending: what was done, what changed, what is blocked, what is next. Update the last updated date and the file index if new files were added.

## Training provenance

Build the training program from the frameworks in `~/.claude/knowledge/books/` (sales, coaching-and-training, negotiation-and-closing, hr, leadership-and-management).

Do not import Bali Exception's internal training material, buying process documents, or contract checklists. Matthieu left BE on 3 October 2026 and BSH is building a competing brokerage. Same frameworks are fine, BE's documents are not.

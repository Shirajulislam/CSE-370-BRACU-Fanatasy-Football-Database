# BRACU CSE-370 Fantasy Football Database

> **Project status:** Historical academic project; recovery and documentation work is in progress. This is not a live NFL data service and has not been validated for production deployment.

This repository contains an academic adaptation of a fantasy-football database project. It brings together relational database schemas and views, SQL queries, data-scraping utilities, statistical analysis scripts, and legacy web interfaces for exploring American football (NFL) data.

The BRACU version was based on the upstream [Fantasy-Football-Database project by edavis25](https://github.com/edavis25/Fantasy-Football-Database). The adaptation should be understood alongside the original project and its authors' notices; it should not be presented as wholly original work.

## Project components

| Path | Purpose |
|---|---|
| `MySQL/` | MySQL schema, views, and conversion notes |
| `SQLite/` | SQLite views for game, team-game, and position statistics |
| `analysis/` | R scripts and saved statistical visualizations |
| `dashboard/` | Legacy PHP dashboard based on the SB Admin / Bootstrap template |
| `data-scrapers/` | Java and R utilities for collecting or processing football data |
| `front-end-website/` | HTML, CSS, JavaScript, and PHP pages for querying game and team statistics |
| `database-tables-schema.sql` | Relational table schema |
| `helpful-snippets.sql` | Example and helper SQL queries |
| `Player-Import-R.txt` | Notes and script material related to player imports |

## Data and coverage

The project includes historical NFL data structures and analysis code. A separate recovered Windows archive contains a populated SQLite database whose game records span **September 8, 2005 to January 1, 2017**. That database snapshot is not currently part of this GitHub repository and has not been added during this documentation update.

The recovered data is historical, not current. Before adding or redistributing the database, CSV exports, or scraped data, document their original sources and confirm that their terms permit redistribution.

## Getting started

This repository currently does not provide one verified, end-to-end setup process for every component. The MySQL and SQLite scripts are separate; do not assume that a script written for one database engine will run unchanged on the other.

Before running any import scripts, read the instructions in the relevant directory. In particular, the 2016 import notes warn that the SQL files should not simply be executed without following their manual reconciliation steps.

The legacy dashboard and website also require a compatible PHP/database environment. Their dependencies and setup instructions still need to be documented and tested. Please treat this repository as a historical codebase under review rather than a ready-to-deploy application.

## Security note

The legacy PHP code contains database connection settings in source files and constructs some SQL queries from request parameters. Do not deploy the dashboard or website publicly until those issues have been addressed. See [SECURITY_REVIEW.md](SECURITY_REVIEW.md) for the initial findings and remediation guidance.

## Attribution and licensing

This is an adaptation of the upstream project at <https://github.com/edavis25/Fantasy-Football-Database>. The supplied SQL schema contains attribution to **Eric Davis** and **Mark Eidsaune**. Preserve upstream notices and add accurate acknowledgements for the BRACU group contributors once their names and roles have been confirmed.

The existing `dashboard/LICENSE` applies to the SB Admin dashboard template and names its original copyright holder. It should not be treated as a project-wide licence for the database, scrapers, website, or datasets. No root-level licence for the complete project has been added as part of this recovery work. See [ATTRIBUTION_AND_LICENSING.md](ATTRIBUTION_AND_LICENSING.md) before making licensing or redistribution changes.

## Contributing

The project is being reviewed and recovered. Contributions should preserve source attribution, identify data sources, avoid committing credentials or private data, and include reproducible checks where practical. See [CONTRIBUTING.md](CONTRIBUTING.md) for the proposed workflow.

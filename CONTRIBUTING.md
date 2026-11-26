# Contributing

Thank you for taking an interest in this project. This repository is a historical academic adaptation of an earlier fantasy-football database project, and it is currently being reviewed and recovered. Please help keep changes transparent, reproducible, and correctly attributed.

## Before contributing

1. Check existing issues and open a new issue for a bug, feature, or documentation change.
2. Identify whether the file you are changing comes from the upstream project, a BRACU group contribution, or a third-party template/library.
3. Preserve copyright notices, licence files, and source citations.
4. Do not add credentials, API keys, private information, or data whose redistribution terms are unclear.

## Development workflow

1. Create a branch from the current default branch.
2. Keep each change focused and explain its purpose.
3. Update documentation when setup, dependencies, schema, or data sources change.
4. Run the relevant checks and include the commands and results in your pull request.
5. Open a pull request describing what changed, why it changed, and what remains unverified.

## Database and data changes

- Keep MySQL and SQLite scripts separate. SQL syntax and behaviour can differ between database engines.
- Read the applicable import instructions before running any data-import script. Some historical import notes describe manual reconciliation steps.
- For schema changes, include a reproducible example or test where practical.
- Record the source, date range, and applicable redistribution terms for every new dataset.
- Do not describe the historical dataset as current NFL coverage.

## Security and code quality

- Use prepared statements for SQL values.
- Validate dynamic table names, column names, and sort directions against explicit allow-lists.
- Escape untrusted values before rendering them into HTML.
- Keep database credentials in environment variables or an untracked local configuration file.
- Avoid committing generated class files, build directories, IDE-private files, or downloaded executables unless there is a documented reason.

## Pull request checklist

- [ ] The change has a clear purpose and limited scope.
- [ ] Existing upstream and third-party notices are preserved.
- [ ] No secrets or private data are included.
- [ ] Relevant checks have been run and described.
- [ ] Documentation and data-source notes are updated.

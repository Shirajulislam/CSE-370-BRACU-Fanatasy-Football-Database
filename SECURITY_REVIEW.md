# Initial security review

**Scope:** Static inspection of the recovered Windows ZIP archive on 2026-11-26. This was not a penetration test. The PHP website and dashboard were not deployed or tested as public services.

## Findings

### 1. Database connection settings are in source code

The recovered archive contains database connection parameters directly in PHP files, including:

- dashboard/resources/database-helper.inc
- front-end-website/php/game-query.php
- front-end-website/php/team-stats-query.php

The values are not reproduced here. They appear to be legacy connection settings; this review did not establish whether any were valid production credentials. If any real or reused password has ever been committed to a public repository, rotate it and review the Git history. Move local settings to environment variables or an untracked configuration file, and use a least-privileged database account.

### 2. Request values are concatenated into SQL

The recovered front-end-website/php/game-query.php builds SQL using values from $_REQUEST, including team names and query filters. Its team-list helper inserts values directly into an SQL IN clause. If this code is exposed to untrusted users, it creates a SQL-injection risk.

Use prepared statements for values. For dynamic table names, column names, and sort directions, use a strict allow-list because SQL identifiers cannot be parameter-bound like ordinary values.

### 3. Dashboard query construction needs validation

The recovered dashboard/resources/database-helper.inc constructs SQL using function arguments for team names, selected columns, ordering fields, and limits. Validate dynamic identifiers and numeric limits against explicit allow-lists and ranges, and use prepared statements for values.

### 4. HTML output should be escaped

The legacy PHP pages insert database values into generated HTML. Escape untrusted values for the appropriate output context (for example, HTML text) to reduce cross-site scripting risk.

### 5. Legacy executables and generated files

The recovered archive includes bundled Windows executables, Java class files, and a JAR. Record their origin and versions. Prefer reproducible, documented dependency installation over committing old executables where practical.

## Recommended remediation order

1. Confirm whether any hardcoded credentials were real or reused; rotate them if so.
2. Move local database settings out of source control.
3. Replace SQL string concatenation with prepared statements and allow-lists.
4. Escape dynamic HTML output.
5. Document supported PHP, Java, R, MySQL, and SQLite versions.
6. Add tests for query handling, schema creation, and key database operations before deployment.

## Validation limitations

This was a source review only. No web server, PHP runtime, MySQL server, Java scraper, or R analysis script was executed. Findings should be rechecked as the code is modernized.

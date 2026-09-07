# Regenerate URL Rewrites for Magento 2 (SISL fork)

A CLI command that regenerates product and category URL rewrites in Magento 2 — the fix
for duplicate, missing or broken URLs after an import, a category move or a migration.

```bash
bin/magento ok:urlrewrites:regenerate
```

Maintained fork of `onestic/magento2-regenerate-url-rewrites` (originally by Oleg Koval),
verified on **Magento 2.4.9 / PHP 8.4**.

## What changed vs upstream

- **`execute(): int` fix** — the console command's `execute()` had no `: int` return type,
  which Symfony Console 7.4 (shipped with Magento 2.4.9) requires. Without it `bin/magento`
  threw a **fatal error** and the whole CLI was unusable. Added the return type and proper
  `Cli::RETURN_SUCCESS` / `RETURN_FAILURE` codes.
- Added `require` to composer.json (`php` 8.1–8.5, `magento/framework >=103.0.4 <104`);
  removed `minimum-stability: alpha`.

## Install

```bash
composer config repositories.regen vcs https://github.com/SISL-source/magento2-regenerate-url-rewrites
composer require onestic/magento2-regenerate-url-rewrites:dev-main
bin/magento setup:upgrade
```

## License

OSL-3.0 / AFL-3.0 (upstream). Maintained by [SISL](https://sisl.pl) — one of a set of revived,
free, open-source Magento modules kept working on the latest releases.

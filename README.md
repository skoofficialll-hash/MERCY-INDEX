# Mercy Index — country site lists

**Data only.** No app code lives here, so country files never clutter the code repo.

## Layout

```
india.json        ← India pack (551 sites)
manifest.json     ← what exists, how big, what sha256
validate.yml      ← every push is checked before it can be used
```

One file per country, named `india.json`, `bd.json`, `lk.json`, `ng.json`, `ke.json`, `id.json`.
The app picks the pack from the phone's country, and falls back to `india.json`.

## Entry format

```json
{"n":"IRCTC","u":"https://www.irctc.co.in","t":"train ticket railway tatkal","c":"travel"}
```

| field | meaning | rule |
|---|---|---|
| `n` | display name | the organisation's own name |
| `u` | url | must start with `https://`, must be the official site |
| `t` | search keywords | 3–8 lowercase words, Hinglish welcome |
| `c` | category | gov, state, money, utility, travel, education, health, shop, info, fun, tool |

## The rule that does not bend

**If a URL is not confirmed, it does not go in.** A missing site is fine. A wrong URL breaks the
one thing this browser sells: trust.

## Adding a country

1. Ask for the list (same prompt, different country).
2. Save it as `<cc>.json` here.
3. Push — `validate.yml` checks https, duplicates, categories, empty keywords.
4. Update `manifest.json` (entries, bytes, sha256, version).
5. Users get it through **Menu → DATA → Update site list**.

## Why a separate repo

- The code repo stays small and readable.
- Lists change weekly; code changes monthly.
- Every list change has its own history, so a bad list can be rolled back without touching the app.

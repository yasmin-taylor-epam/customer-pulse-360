# Copilot instructions for Customer Pulse 360

## Hosted scenario document

- The scenario blueprint document is `site/index.html`.
- Its hosted copy is on GitHub Pages at https://yasmin-taylor-epam.github.io/customer-pulse-360/. The page is public.
- The workflow `.github/workflows/pages.yml` publishes the `site/` folder. It runs on every push to `main` and on manual dispatch.
- Do not publish the page by hand. Do not publish to Lavish or any other host. Merge changes to `main` instead.
- Never put credentials, secrets, or customer records in `site/`.
- To verify the hosted copy after a deploy, check the workflow run and fetch the page:

```powershell
gh run list -R yasmin-taylor-epam/customer-pulse-360 -w pages.yml -L 1
curl.exe -s -o NUL -w "%{http_code}" https://yasmin-taylor-epam.github.io/customer-pulse-360/
```

## Writing style

- Write reader-facing text in clear, concise British English.
- Follow ASD-STE100 structural rules: short sentences, active voice, one idea per sentence.
- Keep chat replies terse (caveman style). Keep every fact, number, and negation.

## Content rules

- Label fictional companies, illustrative cases, and proposed targets as such.
- Cite a source for every market or regulatory fact. Do not invent figures.

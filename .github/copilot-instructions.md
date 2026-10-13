# Copilot instructions for Customer Pulse 360

## Hosted scenario document

- The scenario blueprint document is `site/index.html`.
- The team reviews it as a Lavish artifact. Its hosted copy is at https://efeeb7a1.ht-ml.app (site ID `efeeb7a1`).
- The hosted page is password protected. Do not change or remove the password unless the user asks.
- After you change `site/index.html`, update the hosted copy in place. Do not create a new site.

```powershell
npx -y lavish-axi share site/index.html --site efeeb7a1 --update-key "$([Environment]::GetEnvironmentVariable('LAVISH_CP360_UPDATE_KEY','User'))"
```

- The update key is in the user environment variable `LAVISH_CP360_UPDATE_KEY` on the author's machine.
- Never write the update key into this repository, the HTML, commits, or chat handoffs.
- If the variable is missing, ask the user for the key. Do not publish to a new URL.
- The page password is in the user environment variable `LAVISH_CP360_PASSWORD`. Never write it into this repository.
- To verify the hosted copy after a republish, send the password as the `ht_ml_pwd` cookie:

```powershell
curl.exe -s -b "ht_ml_pwd=$([Environment]::GetEnvironmentVariable('LAVISH_CP360_PASSWORD','User'))" https://efeeb7a1.ht-ml.app/
```

## Writing style

- Write reader-facing text in clear, concise British English.
- Follow ASD-STE100 structural rules: short sentences, active voice, one idea per sentence.
- Keep chat replies terse (caveman style). Keep every fact, number, and negation.

## Content rules

- Label fictional companies, illustrative cases, and proposed targets as such.
- Cite a source for every market or regulatory fact. Do not invent figures.

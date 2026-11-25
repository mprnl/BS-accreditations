# BS-accreditations

Module externe de [BACKSTAGE](https://github.com/mprnl/backstage) : suivi des
demandes d'accréditation photo reçues par mail, fiches de demande et relance
J+7 par notification.

Extrait de `modules/accreditations` après #255. Il ne connaît que le contrat
`@backstage/module-kit` : aucun import de `@/lib/*`.

## Capacités utilisées

- `ctx.mail` : lecture des fils Gmail (`listThreads`, `getThread`, `getMessage`).
- `ctx.notify` : notification de relance.
- `ctx.ai` : extraction des demandes par Groq, via le noyau.

Un hôte qui ne fournit pas `mail` ou `notify` reçoit un refus explicite, jamais
un résultat inventé.

## Installation

Depuis un dépôt BACKSTAGE, avec une ref figée :

```bash
bun run module:add https://github.com/mprnl/BS-accreditations.git#v1.0.0
bun run build
```

Variables d'environnement côté application : `GROQ_API_KEY` (extraction),
`GROQ_API_KEYS` et `GROQ_SCAN_DELAY_MS` en option.

## Licence

MIT.

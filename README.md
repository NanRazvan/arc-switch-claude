# ARC Switch pentru Claude

Un plugin pentru echipa ARC: **skill-ul „fisa-proiect”** (cum se lucrează) + **conectorul ARC** (catalogul și proiectele
din panou). Cătălin încarcă planul sau schema clientului în Claude, iar Claude face proiectul (ciornă în panou), pune
întrebările care lipsesc și dă linkul fișei pentru client.

```
.claude-plugin/marketplace.json        lista pluginurilor (acesta e „magazinul”)
plugins/arc-switch/
  .claude-plugin/plugin.json           numele și versiunea pluginului
  skills/fisa-proiect/SKILL.md         pașii și regulile
  skills/fisa-proiect/tipare.md        cum se citește fiecare fel de document (schemă FEDE, plan, listă …)
  skills/fisa-proiect/vocabular.md     cum se numesc aparatele la alte branduri / în alte limbi
```

Folderul e copiat într-un **repo GitHub separat** (`arc-switch-claude`), din care Claude îl instalează, fără acces la
codul site-ului. Conectorul NU e în plugin: se adaugă o singură dată ca „custom connector” (mai jos), pentru că are
nevoie de o cheie.

## Instalare (o singură dată)

### 1. Cheia contului din panou
Panou › Sistem › Utilizatori › contul folosit de Claude (recomandat unul separat, ex. „claude@arcswitch.ro”, rol
**editor**) › bifează **Enable API Key** › copiază cheia › Save. Debifat = cheia nu mai merge nicăieri.

### 2. Conectorul ARC (în aplicația Claude)
Settings › Connectors › **Add custom connector** (la Team: administratorul, din Organization settings):
- URL: `https://<adresa site-ului>/api/mcp`
- Request headers: `Authorization` = `Bearer <cheia de la pasul 1>`
- cât timp site-ul e protejat de Vercel (până la lansare), încă un antet: `x-vercel-protection-bypass` = secretul din
  Vercel › Project › Settings › Deployment Protection › Protection Bypass for Automation.

### 3. Skill-ul (pluginul)
- **Team**: Organization settings › Plugins & skills › Marketplaces › Add plugins › Sync from GitHub ›
  `NanRazvan/arc-switch-claude` › pluginul `arc-switch`: „Installed by default”. (Sincronizarea pe organizație poate cere
  repo privat: vezi ce acceptă ecranul.)
- **Cont individual (Pro / Max)**: Customize › Plugins › Add › Add marketplace › Add from a repository ›
  `NanRazvan/arc-switch-claude`, apoi Discover › ARC Switch › Add.
- **Claude Code**: `/plugin marketplace add NanRazvan/arc-switch-claude`, apoi `/plugin install arc-switch@arc-switch`;
  conectorul: `claude mcp add --transport http arc https://<adresa>/api/mcp --header "Authorization: Bearer <cheia>"`.

### 4. Încearcă
Conversație nouă: încarcă planul sau schema clientului și scrie „Fă-i fișa pentru <client>”.

## O versiune nouă

1. Schimbi skill-ul / vocabularul.
2. Crești `version` în `plugins/arc-switch/.claude-plugin/plugin.json`.
3. `claude plugin validate plugins/arc-switch` și `claude plugin validate .`
4. Commit + merge în ramura principală: sincronizarea o duce la echipă.

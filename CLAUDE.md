# Skulptur-AR — Meny-app (läs detta först)

Fristående **launcher/meny** för AR-skulptur-installationen. Nås av **1 QR-kod**.
Visar stora ikoner per skulptur; tryck → "Scanna X"-skärm (markörbild transparent)
→ går vidare till den skulpturens egen Vercel-deploy.

Ingen 8th Wall, ingen build — bara statiska filer (`index.html` + `assets/`).
Deployas direkt på Vercel som statisk sida.

## Struktur
- `index.html` — hela appen (HTML/CSS/JS). Config-listan **`SCULPTURES`** överst i
  `<script>` styr allt: per skulptur `name`, `icon`, `marker`, `url`.
- `assets/` — urklippta ikoner + markörbilder (PNG). Filnamn matchar `SCULPTURES`.

## Lägg till / ändra en skulptur
Redigera `SCULPTURES` i `index.html`:
```
{name: 'Vind', icon: 'assets/vind-ikon.png', marker: 'assets/vind-markor.png', url: 'https://...vercel.app/'}
```
- Tom `url` = skulpturen visas nedtonad och går inte att välja (ej klar än).
- Lägg ikon-/markörbilderna i `assets/`.

## Hör ihop med skulptur-apparna (separata repon)
- Varje skulptur är ett eget repo/Vercel-projekt (kopia av "Eld"-projektet).
- Skulptur-appen visar själv "Scanna X" + gör AR:et, och ska gå **tillbaka hit**
  vid ✕ och när musiken tar slut. Det styrs av konstanten **`MENU_URL`** överst i
  skulptur-appens `src/index.html` — sätt den till denna menys URL.

## Deploy
Statisk sida → eget GitHub-repo → Vercel (ingen build behövs, root = denna mapp).

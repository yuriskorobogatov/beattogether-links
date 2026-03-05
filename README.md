# Хостинг для Universal Links — GitHub Pages

## Структура папки `web/`
```
web/
  .well-known/
    apple-app-site-association   ← JSON для iOS (без расширения)
  invite/
    [code].html                  ← fallback-страница (пример)
  index.html                     ← опционально, главная
```

## Шаги публикации (бесплатно, 10 минут)

### 1. Заполни `apple-app-site-association`
Замени `TEAMID` на свой Apple Team ID (найдёшь в developer.apple.com → Membership):
```json
"appIDs": ["TEAMID.com.heartbeat.app"]
```

### 2. Замени App Store ссылку в `invite/[code].html`
После публикации в App Store замени `id000000000` на реальный App ID.

### 3. Создай репозиторий GitHub Pages
```bash
cd web
git init
git remote add origin https://github.com/ВАШ_НИК/beattogether-links.git
git add .
git commit -m "Universal Links support"
git push -u origin main
```
В настройках репозитория → **Pages** → Source: `main / root`

### 4. Привяжи домен `beattogether.app`
В DNS добавь:
```
CNAME  @  ВАШ_НИК.github.io
```
Или используй бесплатный поддомен: `beattogether.YOUR_NICK.github.io` —
тогда замени домен в entitlements и L10n.

### 5. ВАЖНО: HTTPS обязателен
GitHub Pages включает HTTPS автоматически. Файл AASA должен быть доступен по:
`https://beattogether.app/.well-known/apple-app-site-association`
**без редиректа** (iOS проверяет его при установке приложения).

### 6. После деплоя
Можно проверить на: https://branch.io/resources/aasa-validator/

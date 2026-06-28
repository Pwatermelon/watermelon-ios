# Melon iOS / macOS

Нативные клиенты Watermelon Messenger для iPhone, iPad и Mac (SwiftUI + shared API layer).

Репозиторий расположен рядом с основным бэкендом и веб-клиентом:

```
Documents/
├── melon-messenger/   # API, web, deploy
├── melon-ios/         # этот репозиторий
├── melon-android/
└── melon-infra/
```

## Структура

```
melon-ios/
├── Shared/           # Общий Swift-код (API, модели, auth)
├── iOS/              # iPhone / iPad
├── macOS/            # Mac
└── YANDEX_OAUTH.md   # OAuth Yandex ID для native
```

## API

- REST: `{baseURL}/api` (production) или `http://localhost:8080/api` (dev через Docker)
- WebSocket: `{baseURL}/ws`
- Auth: OAuth Yandex → JWT в `Authorization: Bearer`

## Реализовано

- **`WMYandexAuth`** — Yandex OAuth через `ASWebAuthenticationSession`
- `WatermelonCore`: config, authorize URL, code exchange, `WMSessionStore.loginWithYandex()`
- **iOS**: LoginView, beta pending, ChatList + WS
- **macOS**: аналогичный flow
- См. [YANDEX_OAUTH.md](YANDEX_OAUTH.md)

## Следующие шаги

1. Xcode workspace с targets iOS + macOS + URL scheme `watermelon`
2. WebSocket realtime (`WMWebSocket`)
3. TestFlight / App Store

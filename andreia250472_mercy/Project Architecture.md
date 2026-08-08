Its a feature-first architecture combined with a centralized **Core** layer for shared infrastructure

```ASCII
lib/
├── core/     # Cross-cutting concerns & Shared Infrastructure
│   ├── const/  # Global constants (Colors, Icons, Dimensions)
│   ├── gen/               # FlutterGen outputs (Assets, L10n)
│   ├── providers/# Riverpod providers (one file per provider)
│   ├── routes/  # GoRouter configuration (StatefulShellRoute)
│   ├── service/         # Network/Dio,Cache/SharedPreferences
│   └── static/                   # Static data/mock data
├── src/                          # Application source code
│   ├── feature/                  # Feature-based modules
│   │   └── <feature_name>/       # e.g., home, community, ask
│   │       └── presentation/     # UI Layer
│   │           └── <screen>/     # Screen-specific logic
│   │               ├── view/     # UI Widgets/Screens
│   │               ├── view_model/ # Logic/State handling
│   │               └── model/   # Screen-specific data models
│   └── widgets/                 # Shared/Common UI components
└── main.dart           # App entry point & Provider overrides
```

#### Key Notes

- **State Management:**
>**Riverpod** . The `lib/core/providers/` directory houses global state, while feature-specific logic resides in **view_model** directories.

- **Navigation:**
> **GoRouter** with a `StatefulShellRoute.indexedStack` setup for the 3-tab bottom navigation.

- **Theming:**
> A custom **ThemeExtension** system (**`extension`** keyword) is used to avoid hardcoded values, accessible via `context.color`, `context.textStyle`, and `context.dimensions`.

- **Sizing:**
> Responsive design is handled by **flutter_screenutil** (base: 375×812).

- **Networking:**
> **Dio** + **Retrofit** with a TokenManager for automated Bearer token injection and 401 (Unauthorized) refresh handling.

- **Localization:**
> Multi-language support (en, vi) using standard **ARB** files (**l10n**).

---

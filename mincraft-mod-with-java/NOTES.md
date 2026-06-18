# Notes

## User Preferences

- **Dark mode**: All lessons and reference documents must use dark color schemes. Background should be dark (#1a1a2e or similar), text light. Avoid bright white backgrounds.
- **Link Colors**: Hyperlinks must use high-contrast colors (like `#64ffda` teal or similar non-blue brights) because the background is dark blue/purple. Standard `var(--info)` blue blends in too much and is hard to see. Always add underline/border to links so they are clearly identifiable.
- **Version Baseline**: ALL Fabric mod development lessons and code MUST target the Minecraft 26 API (where `BuiltInRegistries` and `ResourceKey` are required, and `Identifier.parse()` is used). Never use the legacy `new Identifier()` or `Registries.ITEM` direct registration. Additionally, all asset generation must respect the Data-Driven Item Model architecture (requiring `items/` definition files).
- **Language**: 中文授課（Traditional Chinese / Mandarin），但程式碼、術語保留英文原文
- **Pace**: Flexible. Start with moderate pacing and adjust based on feedback.

## User Background (for Zone of Proximal Development)

- 3 years as frontend engineer (JS/TS)
- Side project experience with Python FastAPI backend
- Understands REST API design, client-server architecture
- Comfortable with OOP concepts (classes, inheritance, polymorphism)
- Comfortable with async patterns (JS async/await, Python asyncio)
- No prior Java-specific knowledge

## Teaching Approach Preferences

- Prefer learning through building real things over abstract theory
- Minecraft MOD development is the "hook" — keep tying back to it
- SpringBoot is the career endgame — don't lose sight of it
- Avoid re-teaching general programming concepts they already know
- Focus on Java-specific differences and JVM ecosystem
- **"順帶一提" (By-the-way) tips**: Every lesson must include 3–6 "順帶一提" side-knowledge tip boxes scattered throughout. These cover adjacent-but-not-core knowledge — ecosystem comparisons, historical context, best practices, naming conventions, tool comparisons, etc. Use the `.tip` CSS class (purple left-border accent, compact card). The tip label is always "💡 順帶一提：{topic}". This serves to broaden the learner's mental map without bloating the core lesson content. Examples: "Gradle vs Maven", "Fabric vs NeoForge", "JDK distributions", "why main is static".

## Workspace Path Note

The user typed `/mincraft-mod-with-java/` (missing 'e' in 'minecraft'). Keeping this path as-is since they specified it.

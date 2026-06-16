# Architecture Mental Model Established

User completed Lesson 0001 and demonstrated understanding of React Native's three-layer runtime architecture: JS Thread (Hermes), C++ JSI layer, and Native UI Thread. Can distinguish old architecture (Async Bridge with JSON serialization) from new architecture (JSI with synchronous C++ calls, Fabric renderer, TurboModules, Codegen). Understands that RN has no DOM — UI is real native views controlled via C++ bridge, not browser APIs.

**Evidence:** User completed all 5 practice phases up to the free-recall diagram exercise. User explicitly confirmed lesson quality ("蠻好的", "很棒").

**Implications:**
- Ready for hands-on environment setup (Lesson 0002)
- Future lessons can reference the three-layer model without re-explaining
- Key gap remaining: how JSX actually maps to native components (target for Lesson 0003)

# PocketAI Implementation Plan

This branch is the working PocketAI branch. `main` remains an untouched reference to the upstream fork while PocketAI is assembled and validated.

## Goal

PocketAI is a private, local-first iPhone AI assistant with optional hybrid/cloud acceleration.

Core V1 foundation:
- Local text chat with streaming responses
- Local model discovery, download, validation, and import
- Local image generation
- Local voice input/output
- Local vision/image understanding
- Persistent local conversations and memory foundation
- Device memory/thermal safety and model residency controls
- Optional authenticated local API

Later hybrid features:
- User-configurable remote/VPS inference endpoint
- Cloud GPU image/video jobs when local execution is impractical
- Remote video generation as an optional module
- Local-first fallback when remote services are unavailable

## Implementation rules

1. Preserve the MIT license and applicable third-party notices.
2. Do not commit model weights, credentials, signing certificates, provisioning profiles, API keys, or generated native frameworks.
3. Keep `main` usable as the upstream reference; PocketAI work happens on `pocketai` until validated.
4. Preserve runtime cancellation, memory/thermal protection, model validation, and lifecycle cleanup when reusing inference components.
5. Put inference backends behind narrow interfaces so local MLX/llama.cpp and future remote providers can coexist.
6. Keep personal conversations and memory local by default. Remote inference must be explicit and configurable.
7. Do not require an Apple Developer Program membership for initial Simulator validation.

## Build sequence

### Phase 1 — Foundation
- Establish PocketAI branch and project plan.
- Inventory reusable chat, image, voice, vision, model-management, persistence, and safety components.
- Define PocketAI app shell and runtime interfaces.
- Prepare unique PocketAI bundle identifiers and display name in project configuration.
- Preserve original source components while wiring the new target.

### Phase 2 — Local AI
- Wire MLX/llama.cpp text runtime.
- Wire model discovery/download/import.
- Wire conversation persistence.
- Wire image generation.
- Wire vision.
- Wire voice transcription and speech.
- Preserve thermal/memory/lifecycle protections.

### Phase 3 — Hybrid architecture
- Add a provider abstraction for local vs remote inference.
- Add configurable authenticated VPS endpoint support.
- Keep local inference as the privacy-first/default path.
- Add graceful offline behavior and remote failure fallback.

### Phase 4 — Optional video
- Add asynchronous remote video-job interface.
- Keep video generation off-device unless a future device/model makes local generation practical.
- Do not bundle video model weights into the iOS app.

### Phase 5 — Xcode validation
- Generate the Xcode project/workspace.
- Resolve dependencies and build native frameworks.
- Build first in Simulator.
- Configure Joe's Apple development team and signing for physical iPhone testing.
- Install and test on physical iPhone.
- Fix compile/runtime/device-memory issues found during validation.

## Initial identity

Working product name: **PocketAI**

Planned private-development bundle identifiers:
- App: `com.joemullins.pocketai`
- Tests: `com.joemullins.pocketai.tests`

These can be changed later if Apple signing requires a different identifier.

## Current status

- [x] Fork created under `boomersoonerjoe/ios-local-llm`
- [x] Dedicated `pocketai` development branch created
- [x] Upstream architecture and fork requirements reviewed
- [x] PocketAI implementation plan added
- [ ] PocketAI app target assembled
- [ ] Local chat wired
- [ ] Model management wired
- [ ] Image generation wired
- [ ] Voice wired
- [ ] Vision wired
- [ ] Persistence/memory wired
- [ ] Hybrid provider interface wired
- [ ] Ready for first Xcode build

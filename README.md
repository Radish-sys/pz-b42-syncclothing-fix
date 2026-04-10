# pz-b42-syncclothing-fix

A patch for a crash in Project Zomboid Build 42.16.3 that disconnects clients when hitting zombies in multiplayer.

## The Bug

`SyncClothingPacket$ItemDescription` throws a `NullPointerException` when `getVisual()` returns null on a worn item during combat. This crashes the client and disconnects them from the server.

## The Fix

Null checks added in `SyncClothingPacket.java` before calling `getTint()`, `setTint()`, `setBaseTexture()`, and `setTextureChoice()` on item visuals.

## How to Apply

1. Back up your original `projectzomboid.jar` (found in your PZ install's `java` folder)
2. Download the patched `projectzomboid.jar` from the [latest release](https://github.com/Radish-sys/pz-b42-syncclothing-fix/releases/latest)
3. Navigate to your PZ install folder (Steam → right click Project Zomboid → Manage → Browse local files → `java` folder)
4. Replace `projectzomboid.jar` with the downloaded one

> **Note:** Steam updates will overwrite this fix. Re-apply after each PZ update until TIS patches it officially.

## Transparency

The patched source `SyncClothingPacket.java` is included in the release assets. You can verify the changes yourself by decompiling the jar with [CFR](https://github.com/leibnitz27/cfr).

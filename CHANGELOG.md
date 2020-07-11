# Changelog

All notable changes should be documented in this file. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## 4.9.3.3 - 2020-07-10

### Changed
- The command to reload all plugins at once has been disabled by popular request. Many plugins did not support it properly. Reloading individual plugins is still enabled. Read this issue for more details: [#1794](https://github.com/SmartlyDressedGames/Unturned-3.x-Community/issues/1794)
- `Logger` console output is routed through Unturned's `CommandWindow` class, rather than directly using the `System.Console` class. This fixes Rocket output blocking the game thread. Reported by @rube200 in issue #21.

## 4.9.3.2 - 2020-05-18

### Changed
- Home command offsets vertically similar to the vanilla respawn, and warns player when unable to teleport.

## 4.9.3.1 - 2020-05-15

### Changed
- `AutomaticSaveWatchdog` checks the timer during `Update` rather than `FixedUpdate` because the latter is for physics code. Reported by @rube200 in PR #7.
- `UnturnedChat` internally uses `ChatManager.serverSendMessage` rather than manually invoking the `tellChat` RPC. 
- Marked Observatory obsolete and deleted the implementation because it is no longer maintained. Reported by DiFFoZ in PR #4.

### Fixed
- `UnturnedPlayer.Ban` correctly calls `Provider.requestBanPlayer` rather than `Provider.ban`. The distinction is that `requestBanPlayer` allows plugins to override the ban handling and saves the ban information, whereas `ban` is a poorly named internal callback. Reported by @Kr4ken-9 in PR #1.
- `UnturnedPlayer` overrides `Object.Equals` and `Object.GetHashCode` in order to work properly with standard containers. Reported by @CyberAndrii in PR #2.
- `UnturnedPlayerComponent` no longer calls `DontDestroyOnLoad` on itself. This component exists per-player and should be destroyed during level load. Reported by @rube200 in PR #7.
- `UnturnedChat` was ignoring the `rich` parameter. Reported by @Tortellio and @CyberAndrii.

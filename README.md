# Lavalink
A standalone audio sending node based on Lavaplayer and JDA-Audio.
Allows for sending audio without it ever reaching any of your shards.

Being used in production by FredBoat, Dyno, LewdBot, and more.

A [basic example bot](Testbot) is available.

[![JDA guild](https://discordapp.com/api/guilds/125227483518861312/embed.png?style=banner2)](https://discord.gg/jtAWrzU)

## Features
* Powered by Lavaplayer
* Minimal CPU/memory footprint
* Twitch/YouTube stream support
* Event system
* Seeking
* Volume control
* REST API for resolving lavaplayer tracks (used for non-JVM clients)
* Statistics (good for load balancing)
* Basic authentication
* Prometheus metrics
* Docker images

## Requirements

* Java 11* LTS or newer required.
* OpenJDK or Zulu running on Linux AMD64 is officially supported.

Support for Darwin (Mac), Windows AMD64, and Linux ARM (Raspberry Pi) is provided on a best-effort basis. This is dependent on Lavaplayer's native libraries.

Support for other JVMs is also best-effort. Periodic CPU utilization stats are prone not to work everywhere.

**\*Java 11 appears to have some issues with Discord's TLS 1.3. Java 14 has other undiagnosed HTTPS problems. Use Java 13. Docker images have been updated.** See [#258](https://github.com/freyacodes/Lavalink/issues/258), [#260](https://github.com/freyacodes/Lavalink/issues/260)

## Changelog

Please see [here](CHANGELOG.md)

## Versioning policy

- The public API ("API" in a very broad sense) of Lavalink can be categorized into two main domains:
  - **Client Domain:** The API exposed to clients, consisting of both the WebSocket protocol and any public HTTP endpoints
  - **Server Domain:** The server application with its runtime environment, its configuration, etc.

- A change that is breaking to one domain might not be breaking at all to another.

  *Examples:*
  - Removing an endpoint: This is a breaking change for the client domain but is not for running the server itself.
  - Upgrading the minimum Java version: This is a breaking change for the server domain, but client implementations couldn't care less about it.

**Given the above, the following versioning pattern lends itself well to the Lavalink project:**

_**api.major.minor.patch**_

- **API**: Bumped when breaking changes are committed to the client domain of Lavalink

  *Examples:* Removing an endpoint, altering the output of an endpoint in a non-backward-compatible manner
- **Major**: Bumped when breaking changes are committed to the Lavalink server domain

  *Examples:* Bumping the required Java version, altering the configuration in a non-backward-compatible manner
- **Minor**: New features in any domain

  *Examples:* New optional endpoint or opcode, additional configuration options, change of large subsystems or dependencies
- **Patch**: Bug fixes in any domain

Examples: Fixing a race condition, fixing unexpected exceptions, fixing output that is not according to specs, etc.

While major, minor and patch will do an optimum effort to adhere to [Semantic Versioning](https://semver.org/), prepending it with an additional API version makes life easier for developers in two ways: It is a clear way for the Lavalink project to communicate the relevant breaking changes to client developers, and in return, client developers can use the API version to communicate to their users about the compatibility of their clients to the Lavalink server.


## Client libraries:
* [Lavalink-Client](https://github.com/freyacodes/lavalink-client) (JDA or generic, Java)
* [Lavalink.kt](https://github.com/DRSchlaubi/lavalink.kt) (Kord, JDA, generic, Kotlin (Coroutines))
* [Lavalink.py](https://github.com/Devoxin/Lavalink.py) (discord.py, Python)
* [Lavapy](https://github.com/Aspect1103/Lavapy) (discord.py, Python)
* [pylava](https://github.com/Pandentia/pylava) (discord.py, Python)
* [playlink](https://github.com/OverleapCo/Playlink) (Javascript/Typescript)
* [SandySounds](https://github.com/MrJohnCoder/SandySounds) (JavaScript)
* [Gorilink](https://github.com/Gorillas-Team/Gorilink) (JavaScript)
* [eris-lavalink](https://github.com/briantanner/eris-lavalink) ([eris](https://github.com/abalabahaha/eris), JavaScript)
* [LavaClient](https://github.com/lavaclient/lavaclient) (JavaScript)
* [Shoukaku](https://github.com/Deivu/Shoukaku) ([discord.js](https://github.com/discordjs/discord.js), JavaScript)
* [SpringLink](https://github.com/knyaoo/springlink) ([discord.js](https://github.com/discordjs/discord.js), JavaScript)
* [erela.js](https://github.com/MenuDocs/erela.js) (JavaScript)
* [Lavacord](https://github.com/lavacord/lavacord) (JavaScript)
* [Lavacoffee](https://github.com/XzFirzal/lavacoffee) (JavaScript) 
* [LavaJS](https://github.com/OverleapCo/LavaJS) ([discord.js](https://github.com/discordjs/discord.js), JavaScript/TypeScript)
* [@skyra/audio](https://github.com/skyra-project/audio) ([discord.js](https://github.com/discordjs/discord.js), JavaScript/TypeScript)
* [EvoLava](https://github.com/EvolveJS/EvoLava) ([EvolveJS](https://github.com/EvolveJS/EvolveJS), Javascript/Typescript)
* [SharpLink](https://github.com/Devoxin/SharpLink) ([Discord.Net](https://github.com/RogueException/Discord.Net), .NET)
* [Victoria](https://github.com/Yucked/Victoria) ([Discord.NET](https://github.com/RogueException/Discord.Net), .NET)
* [Lavalink.NET](https://github.com/Dev-Yukine/Lavalink.NET) (.NET)
* [DSharpPlus.Lavalink](https://github.com/DSharpPlus/DSharpPlus/tree/master/DSharpPlus.Lavalink) ([DSharpPlus](https://github.com/DSharpPlus/DSharpPlus/), .NET)
* [Lavalink4NET](https://github.com/angelobreuer/Lavalink4NET) ([Discord.Net](https://github.com/RogueException/Discord.Net), [DSharpPlus](https://github.com/DSharpPlus/DSharpPlus/), .NET)
* [gavalink](https://github.com/foxbot/gavalink) (Go)
* [waterlink](https://github.com/lukasl-dev/waterlink) (Go)
* [Magma](https://github.com/initzx/magma/) (discord.py, Python)
* [WaveLink](https://github.com/EvieePy/Wavelink) (discord.py, Python)
* [Lavalink-rs](https://gitlab.com/vicky5124/lavalink-rs/) (All `tokio` Libraries, Rust)
* [lavasnek_rs](https://github.com/vicky5124/lavasnek_rs/) (All `asyncio` Libraries, Python)
* [Pomice](https://github.com/cloudwithax/pomice) (discord.py, Python)
* [lavaplayer-py](https://github.com/HazemMeqdad/lavaplayer) (All `asyncio` libs, Python)
* Or [create your own](https://github.com/freyacodes/Lavalink/blob/master/IMPLEMENTATION.md)

## Server configuration
Download binaries from [the CI server](https://ci.fredboat.com/viewLog.html?buildId=lastSuccessful&buildTypeId=Lavalink_Build&tab=artifacts&guest=1) or [the GitHub releases](https://github.com/freyacodes/Lavalink/releases).

Put an `application.yml` file in your working directory. ([Example here](https://github.com/freyacodes/Lavalink/blob/master/LavalinkServer/application.yml.example))

Run with `java -jar Lavalink.jar`

Docker images are available on the [Docker Hub](https://hub.docker.com/r/fredboat/lavalink/).

[![Docker Pulls](https://img.shields.io/docker/pulls/fredboat/lavalink.svg)](https://hub.docker.com/r/fredboat/lavalink/) [![Docker layers](https://images.microbadger.com/badges/image/fredboat/lavalink:dev.svg)](https://microbadger.com/images/fredboat/lavalink:dev "Get your own image badge on microbadger.com")

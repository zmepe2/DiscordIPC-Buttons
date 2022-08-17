[version]: https://api.bintray.com/packages/jagrosh/maven/DiscordIPC/images/download.svg
[download]: https://bintray.com/jagrosh/maven/DiscordIPC/_latestVersion
[license]: https://img.shields.io/badge/License-Apache%202.0-lightgrey.svg

[ ![license][] ](https://github.com/jagrosh/DiscordIPC/tree/master/LICENSE)

# DiscordIPC with Buttons

Connect locally to the Discord client using IPC for a subset of RPC features like Rich Presence and Activity Join/Spectate


# Features

- Setting Rich Presence
- Buttons
- Detect and specify priority for client build (Stable, PTB, Canary)
- 100% Java


# Getting Started

First you'll need to add this project as a dependency. If you're using maven:
```xml
  <dependency>
    <groupId>me.cutenyami</groupId>
    <artifactId>DiscordIPC-Buttons</artifactId>
    <version>1.0.0</version>
  </dependency>
```
```xml
  <repository>
    <url>https://tykopvp.com</url>
  </repository>
```
With gradle:
```groovy
dependencies {
    compileOnly 'me.cutenyami:DiscordIPC-Buttons:1.0.0'
}

repositories {
    maven {
        url = "https://tykopvp.com"
    }
}
```

# Example

Quick example, assuming you already have a GUI application
```java
IPCClient client = new IPCClient(345229890980937739L); // your client id
client.setListener(new IPCListener() {
    @Override
    public void onReady(IPCClient client) {
        RichPresence.Builder builder = new RichPresence.Builder();
        builder.setState("State")
            .setDetails("Details")
            .setButton1Text("Discord")
            .setButton1Url("https://discord.com")
            .setButton2Text("Google")
            .setButton2Url("https://google.com")
            .setStartTimestamp(OffsetDateTime.now())
            .setLargeImage("canary-large", "Discord Canary")
            .setSmallImage("ptb-small", "Discord PTB");
        client.sendRichPresence(builder.build());
    }
});
client.connect();
```

# Official Discord-RPC Bindings

The official RPC bindings can be found here: https://github.com/discordapp/discord-rpc

A Java wrapper for the official bindings is available here: https://github.com/MinnDevelopment/Java-DiscordRPC

---
title: 重大變更： SignalR： MessagePack Hub 通訊協定選項類型已變更
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 SignalR： MessagePack 中樞通訊協定選項類型已變更
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b75dbec834699472f18b3058052274476bd9751d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760786"
---
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>SignalR： MessagePack Hub 通訊協定選項類型已變更

ASP.NET Core SignalR MessagePack Hub 通訊協定選項類型已從變更 `IList<MessagePack.IFormatterResolver>` 為 [MessagePack](https://www.nuget.org/packages/MessagePack) 程式庫的 `MessagePackSerializerOptions` 類型。

如需此變更的討論，請參閱 [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 4

## <a name="old-behavior"></a>舊的行為

您可以新增至選項，如下列範例所示：

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

並取代這些選項，如下所示：

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

## <a name="new-behavior"></a>新的行為

您可以新增至選項，如下列範例所示：

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

並取代這些選項，如下所示：

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

## <a name="reason-for-change"></a>變更的原因

這項變更是移至 MessagePack v2. x 的一部分，這是在 [aspnet/公告 # 404](https://github.com/aspnet/Announcements/issues/404)中宣告的。 V2 程式庫已新增更容易使用的選項 API，並提供比之前公開的清單更多的功能 `MessagePack.IFormatterResolver` 。

## <a name="recommended-action"></a>建議的動作

這項中斷性變更會影響正在設定值的任何人 <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> 。 如果您使用 ASP.NET Core SignalR MessagePack Hub 通訊協定和修改選項，請更新您的使用方式以使用新的 options API，如上所示。

## <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

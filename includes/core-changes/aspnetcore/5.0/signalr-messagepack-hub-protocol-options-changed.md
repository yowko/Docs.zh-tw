---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507068"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>SignalR： MessagePack 中樞通訊協定選項類型已變更

ASP.NET Core SignalR MessagePack Hub 通訊協定選項類型已從變更 `IList<MessagePack.IFormatterResolver>` 為[MessagePack](https://www.nuget.org/packages/MessagePack)程式庫的 `MessagePackSerializerOptions` 類型。

如需這種變更的討論，請參閱[dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 4

#### <a name="old-behavior"></a>舊的行為

您可以將加入至選項，如下列範例所示：

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

並取代選項，如下所示：

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

#### <a name="new-behavior"></a>新的行為

您可以將加入至選項，如下列範例所示：

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

並取代選項，如下所示：

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

#### <a name="reason-for-change"></a>變更的原因

這項變更是移至 MessagePack v2. x 的一部分，已在[aspnet/公告 # 404](https://github.com/aspnet/Announcements/issues/404)中宣佈。 V2. x 程式庫已加入更容易使用的選項 API，並提供比以前公開的更多功能 `MessagePack.IFormatterResolver` 。

#### <a name="recommended-action"></a>建議的動作

這種中斷性變更會影響在上設定值的任何人 <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> 。 如果您使用 ASP.NET Core SignalR MessagePack Hub 通訊協定並修改選項，請更新您的使用方式，以使用新的選項 API，如上所示。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

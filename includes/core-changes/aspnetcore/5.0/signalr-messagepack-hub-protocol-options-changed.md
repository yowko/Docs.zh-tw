---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507068"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="1fdef-101">SignalR： MessagePack 中樞通訊協定選項類型已變更</span><span class="sxs-lookup"><span data-stu-id="1fdef-101">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="1fdef-102">ASP.NET Core SignalR MessagePack Hub 通訊協定選項類型已從`IList<MessagePack.IFormatterResolver>`變更為[MessagePack](https://www.nuget.org/packages/MessagePack)程式庫的`MessagePackSerializerOptions`類型。</span><span class="sxs-lookup"><span data-stu-id="1fdef-102">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="1fdef-103">如需這種變更的討論，請參閱[dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506)。</span><span class="sxs-lookup"><span data-stu-id="1fdef-103">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1fdef-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1fdef-104">Version introduced</span></span>

<span data-ttu-id="1fdef-105">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="1fdef-105">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1fdef-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1fdef-106">Old behavior</span></span>

<span data-ttu-id="1fdef-107">您可以將加入至選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1fdef-107">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="1fdef-108">並取代選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1fdef-108">And replace the options as follows:</span></span>

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

#### <a name="new-behavior"></a><span data-ttu-id="1fdef-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="1fdef-109">New behavior</span></span>

<span data-ttu-id="1fdef-110">您可以將加入至選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1fdef-110">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="1fdef-111">並取代選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1fdef-111">And replace the options as follows:</span></span>

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

#### <a name="reason-for-change"></a><span data-ttu-id="1fdef-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1fdef-112">Reason for change</span></span>

<span data-ttu-id="1fdef-113">這項變更是移至 MessagePack v2. x 的一部分，已在[aspnet/公告 # 404](https://github.com/aspnet/Announcements/issues/404)中宣佈。</span><span class="sxs-lookup"><span data-stu-id="1fdef-113">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="1fdef-114">V2. x 程式庫已加入更容易使用的選項 API，並提供比`MessagePack.IFormatterResolver`以前公開的更多功能。</span><span class="sxs-lookup"><span data-stu-id="1fdef-114">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1fdef-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1fdef-115">Recommended action</span></span>

<span data-ttu-id="1fdef-116">這種中斷性變更會影響在上設定<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>值的任何人。</span><span class="sxs-lookup"><span data-stu-id="1fdef-116">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="1fdef-117">如果您使用 ASP.NET Core SignalR MessagePack Hub 通訊協定並修改選項，請更新您的使用方式，以使用新的選項 API，如上所示。</span><span class="sxs-lookup"><span data-stu-id="1fdef-117">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

#### <a name="category"></a><span data-ttu-id="1fdef-118">類別</span><span class="sxs-lookup"><span data-stu-id="1fdef-118">Category</span></span>

<span data-ttu-id="1fdef-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1fdef-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1fdef-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1fdef-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

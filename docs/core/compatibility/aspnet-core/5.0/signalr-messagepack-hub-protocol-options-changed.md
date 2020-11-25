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
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="52a88-103">SignalR： MessagePack Hub 通訊協定選項類型已變更</span><span class="sxs-lookup"><span data-stu-id="52a88-103">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="52a88-104">ASP.NET Core SignalR MessagePack Hub 通訊協定選項類型已從變更 `IList<MessagePack.IFormatterResolver>` 為 [MessagePack](https://www.nuget.org/packages/MessagePack) 程式庫的 `MessagePackSerializerOptions` 類型。</span><span class="sxs-lookup"><span data-stu-id="52a88-104">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="52a88-105">如需此變更的討論，請參閱 [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506)。</span><span class="sxs-lookup"><span data-stu-id="52a88-105">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="52a88-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="52a88-106">Version introduced</span></span>

<span data-ttu-id="52a88-107">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="52a88-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="52a88-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="52a88-108">Old behavior</span></span>

<span data-ttu-id="52a88-109">您可以新增至選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="52a88-109">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="52a88-110">並取代這些選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="52a88-110">And replace the options as follows:</span></span>

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

## <a name="new-behavior"></a><span data-ttu-id="52a88-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="52a88-111">New behavior</span></span>

<span data-ttu-id="52a88-112">您可以新增至選項，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="52a88-112">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="52a88-113">並取代這些選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="52a88-113">And replace the options as follows:</span></span>

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

## <a name="reason-for-change"></a><span data-ttu-id="52a88-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="52a88-114">Reason for change</span></span>

<span data-ttu-id="52a88-115">這項變更是移至 MessagePack v2. x 的一部分，這是在 [aspnet/公告 # 404](https://github.com/aspnet/Announcements/issues/404)中宣告的。</span><span class="sxs-lookup"><span data-stu-id="52a88-115">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="52a88-116">V2 程式庫已新增更容易使用的選項 API，並提供比之前公開的清單更多的功能 `MessagePack.IFormatterResolver` 。</span><span class="sxs-lookup"><span data-stu-id="52a88-116">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="52a88-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="52a88-117">Recommended action</span></span>

<span data-ttu-id="52a88-118">這項中斷性變更會影響正在設定值的任何人 <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> 。</span><span class="sxs-lookup"><span data-stu-id="52a88-118">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="52a88-119">如果您使用 ASP.NET Core SignalR MessagePack Hub 通訊協定和修改選項，請更新您的使用方式以使用新的 options API，如上所示。</span><span class="sxs-lookup"><span data-stu-id="52a88-119">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="52a88-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="52a88-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

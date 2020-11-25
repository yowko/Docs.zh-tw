---
title: 重大變更： SignalR： MessagePack Hub 通訊協定已移至 MessagePack 2.x 套件
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 SignalR： MessagePack Hub Protocol 已移至 MessagePack 2.x 套件
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1e666c40d7046233c9fb06af819b901fd1251b06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760785"
---
# <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="19687-103">SignalR： MessagePack Hub 通訊協定已移至 MessagePack 2.x 套件</span><span class="sxs-lookup"><span data-stu-id="19687-103">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="19687-104">ASP.NET Core SignalR [MessagePack Hub 通訊協定](/aspnet/core/signalr/messagepackhubprotocol) 會使用 [MessagePack NuGet 套件](https://www.nuget.org/packages/MessagePack) 進行 MessagePack 序列化。</span><span class="sxs-lookup"><span data-stu-id="19687-104">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="19687-105">ASP.NET Core 5.0 會將套件從1.x 升級到最新的2.x 套件版本。</span><span class="sxs-lookup"><span data-stu-id="19687-105">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="19687-106">如需此問題的討論，請參閱 [dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692)。</span><span class="sxs-lookup"><span data-stu-id="19687-106">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="19687-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="19687-107">Version introduced</span></span>

<span data-ttu-id="19687-108">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="19687-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="19687-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="19687-109">Old behavior</span></span>

<span data-ttu-id="19687-110">ASP.NET Core SignalR 使用 MessagePack 1.x 套件來序列化和還原序列化 MessagePack 訊息。</span><span class="sxs-lookup"><span data-stu-id="19687-110">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="19687-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="19687-111">New behavior</span></span>

<span data-ttu-id="19687-112">ASP.NET Core SignalR 會使用 MessagePack 2.x 套件來序列化和還原序列化 MessagePack 訊息。</span><span class="sxs-lookup"><span data-stu-id="19687-112">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="19687-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="19687-113">Reason for change</span></span>

<span data-ttu-id="19687-114">MessagePack 2.x 套件中的最新改良功能可新增有用的功能。</span><span class="sxs-lookup"><span data-stu-id="19687-114">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="19687-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="19687-115">Recommended action</span></span>

<span data-ttu-id="19687-116">此重大變更適用于：</span><span class="sxs-lookup"><span data-stu-id="19687-116">This breaking change applies when:</span></span>

* <span data-ttu-id="19687-117">設定或設定上的值 <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> 。</span><span class="sxs-lookup"><span data-stu-id="19687-117">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="19687-118">直接使用 MessagePack Api，並在相同專案中使用 ASP.NET Core SignalR MessagePack Hub 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="19687-118">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="19687-119">將會載入較新的版本，而不是先前的版本。</span><span class="sxs-lookup"><span data-stu-id="19687-119">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="19687-120">如需封裝作者的遷移指導方針，請參閱 [從 MessagePack v1. x 遷移至 MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)。</span><span class="sxs-lookup"><span data-stu-id="19687-120">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="19687-121">訊息序列化和還原序列化的某些層面會受到影響。</span><span class="sxs-lookup"><span data-stu-id="19687-121">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="19687-122">具體而言， [日期時間值的序列化方式有一些行為變更](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。</span><span class="sxs-lookup"><span data-stu-id="19687-122">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="19687-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="19687-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345231"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="4c830-101">信號R：MessagePack集線器協定移動到消息包 2.x 包</span><span class="sxs-lookup"><span data-stu-id="4c830-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="4c830-102">ASP.NET核心信號R[消息包集線器協定](/aspnet/core/signalr/messagepackhubprotocol)使用[MessagePack NuGet 包](https://www.nuget.org/packages/MessagePack)進行消息包序列化。</span><span class="sxs-lookup"><span data-stu-id="4c830-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="4c830-103">ASP.NET Core 5.0 將包從 1.x 升級到最新的 2.x 包版本。</span><span class="sxs-lookup"><span data-stu-id="4c830-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="4c830-104">有關此問題的討論，請參閱[dotnet/aspnetcore_18692](https://github.com/dotnet/aspnetcore/issues/18692)。</span><span class="sxs-lookup"><span data-stu-id="4c830-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4c830-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="4c830-105">Version introduced</span></span>

<span data-ttu-id="4c830-106">5.0 預覽 1</span><span class="sxs-lookup"><span data-stu-id="4c830-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4c830-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="4c830-107">Old behavior</span></span>

<span data-ttu-id="4c830-108">ASP.NET核心信號R使用 MessagePack 1.x 包對消息包進行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="4c830-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4c830-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="4c830-109">New behavior</span></span>

<span data-ttu-id="4c830-110">ASP.NET核心信號R使用 MessagePack 2.x 包對消息包進行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="4c830-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4c830-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="4c830-111">Reason for change</span></span>

<span data-ttu-id="4c830-112">MessagePack 2.x 包中的最新改進增加了有用的功能。</span><span class="sxs-lookup"><span data-stu-id="4c830-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4c830-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4c830-113">Recommended action</span></span>

<span data-ttu-id="4c830-114">此重大更改適用于：</span><span class="sxs-lookup"><span data-stu-id="4c830-114">This breaking change applies when:</span></span>

* <span data-ttu-id="4c830-115">設置或配置 上<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>的值。</span><span class="sxs-lookup"><span data-stu-id="4c830-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="4c830-116">直接使用 MessagePack API，並在同一專案中使用ASP.NET核心信號R 消息包集線器協定。</span><span class="sxs-lookup"><span data-stu-id="4c830-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="4c830-117">將載入較新版本，而不是以前的版本。</span><span class="sxs-lookup"><span data-stu-id="4c830-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="4c830-118">有關包作者的遷移指南，請參閱[從 MessagePack v1.x 遷移到 MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)。</span><span class="sxs-lookup"><span data-stu-id="4c830-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="4c830-119">消息序列化和反序列化的某些方面受到影響。</span><span class="sxs-lookup"><span data-stu-id="4c830-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="4c830-120">具體來說，[日期時間值的序列化方式存在行為變化](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。</span><span class="sxs-lookup"><span data-stu-id="4c830-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="4c830-121">類別</span><span class="sxs-lookup"><span data-stu-id="4c830-121">Category</span></span>

<span data-ttu-id="4c830-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4c830-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4c830-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4c830-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

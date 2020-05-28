---
ms.openlocfilehash: ca0792a3fd05d28cecceac1d644e3e4bf64722bc
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345231"
---
### <a name="signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package"></a><span data-ttu-id="8c134-101">SignalR： MessagePack 中樞通訊協定已移至 MessagePack 2.x 套件</span><span class="sxs-lookup"><span data-stu-id="8c134-101">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>

<span data-ttu-id="8c134-102">ASP.NET Core SignalR [MessagePack Hub 通訊協定](/aspnet/core/signalr/messagepackhubprotocol)會使用[MessagePack NuGet 封裝](https://www.nuget.org/packages/MessagePack)來進行 MessagePack 序列化。</span><span class="sxs-lookup"><span data-stu-id="8c134-102">The ASP.NET Core SignalR [MessagePack Hub Protocol](/aspnet/core/signalr/messagepackhubprotocol) uses the [MessagePack NuGet package](https://www.nuget.org/packages/MessagePack) for MessagePack serialization.</span></span> <span data-ttu-id="8c134-103">ASP.NET Core 5.0 會將套件從1.x 升級到最新的2.x 套件版本。</span><span class="sxs-lookup"><span data-stu-id="8c134-103">ASP.NET Core 5.0 upgrades the package from 1.x to the latest 2.x package version.</span></span>

<span data-ttu-id="8c134-104">如需此問題的討論，請參閱[dotnet/aspnetcore # 18692](https://github.com/dotnet/aspnetcore/issues/18692)。</span><span class="sxs-lookup"><span data-stu-id="8c134-104">For discussion on this issue, see [dotnet/aspnetcore#18692](https://github.com/dotnet/aspnetcore/issues/18692).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c134-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="8c134-105">Version introduced</span></span>

<span data-ttu-id="8c134-106">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="8c134-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8c134-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="8c134-107">Old behavior</span></span>

<span data-ttu-id="8c134-108">ASP.NET Core SignalR 使用 MessagePack 1.x 封裝來序列化和還原序列化 MessagePack 訊息。</span><span class="sxs-lookup"><span data-stu-id="8c134-108">ASP.NET Core SignalR used the MessagePack 1.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8c134-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="8c134-109">New behavior</span></span>

<span data-ttu-id="8c134-110">ASP.NET Core SignalR 會使用 MessagePack 2.x 封裝來序列化和還原序列化 MessagePack 訊息。</span><span class="sxs-lookup"><span data-stu-id="8c134-110">ASP.NET Core SignalR uses the MessagePack 2.x package to serialize and deserialize MessagePack messages.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c134-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="8c134-111">Reason for change</span></span>

<span data-ttu-id="8c134-112">MessagePack 2.x 套件中的最新改進功能會新增有用的功能。</span><span class="sxs-lookup"><span data-stu-id="8c134-112">The latest improvements in the MessagePack 2.x package add useful functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c134-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8c134-113">Recommended action</span></span>

<span data-ttu-id="8c134-114">這種重大變更適用于下列情況：</span><span class="sxs-lookup"><span data-stu-id="8c134-114">This breaking change applies when:</span></span>

* <span data-ttu-id="8c134-115">設定或設定上的值 <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> 。</span><span class="sxs-lookup"><span data-stu-id="8c134-115">Setting or configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span>
* <span data-ttu-id="8c134-116">直接使用 MessagePack Api，並在相同的專案中使用 ASP.NET Core SignalR MessagePack Hub 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="8c134-116">Using the MessagePack APIs directly and using the ASP.NET Core SignalR MessagePack Hub Protocol in the same project.</span></span> <span data-ttu-id="8c134-117">將會載入較新的版本，而不是先前的版本。</span><span class="sxs-lookup"><span data-stu-id="8c134-117">The newer version will be loaded instead of the previous version.</span></span>

<span data-ttu-id="8c134-118">如需封裝作者的遷移指導方針，請參閱[從 MessagePack V1 遷移至 MessagePack v2. x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md)。</span><span class="sxs-lookup"><span data-stu-id="8c134-118">For migration guidance from the package authors, see [Migrating from MessagePack v1.x to MessagePack v2.x](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md).</span></span> <span data-ttu-id="8c134-119">訊息序列化和還原序列化的某些層面會受到影響。</span><span class="sxs-lookup"><span data-stu-id="8c134-119">Some aspects of message serialization and deserialization are affected.</span></span> <span data-ttu-id="8c134-120">具體而言，[日期時間值的序列化方式有行為變更](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes)。</span><span class="sxs-lookup"><span data-stu-id="8c134-120">Specifically, there are [behavioral changes to how DateTime values are serialized](https://github.com/neuecc/MessagePack-CSharp/blob/master/doc/migration.md#behavioral-changes).</span></span>

#### <a name="category"></a><span data-ttu-id="8c134-121">類別</span><span class="sxs-lookup"><span data-stu-id="8c134-121">Category</span></span>

<span data-ttu-id="8c134-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8c134-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c134-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8c134-123">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->

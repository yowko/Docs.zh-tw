---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901918"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="2455d-101">信號R：已刪除集線器連接重置發送和重置超時方法</span><span class="sxs-lookup"><span data-stu-id="2455d-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="2455d-102">和`ResetSendPing``ResetTimeout`方法從 SignalR `HubConnection` API 中刪除。</span><span class="sxs-lookup"><span data-stu-id="2455d-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="2455d-103">這些方法最初隻供內部使用，但在ASP.NET核心2.2中公開。</span><span class="sxs-lookup"><span data-stu-id="2455d-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="2455d-104">這些方法在ASP.NET酷睿 3.0 預覽版 4 版中不可用。</span><span class="sxs-lookup"><span data-stu-id="2455d-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="2455d-105">有關討論，請參閱[點網/阿斯平核心#8543](https://github.com/dotnet/aspnetcore/issues/8543)。</span><span class="sxs-lookup"><span data-stu-id="2455d-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2455d-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="2455d-106">Version introduced</span></span>

<span data-ttu-id="2455d-107">3.0</span><span class="sxs-lookup"><span data-stu-id="2455d-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2455d-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="2455d-108">Old behavior</span></span>

<span data-ttu-id="2455d-109">API 可用。</span><span class="sxs-lookup"><span data-stu-id="2455d-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2455d-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="2455d-110">New behavior</span></span>

<span data-ttu-id="2455d-111">將刪除 API。</span><span class="sxs-lookup"><span data-stu-id="2455d-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2455d-112">更改原因</span><span class="sxs-lookup"><span data-stu-id="2455d-112">Reason for change</span></span>

<span data-ttu-id="2455d-113">這些方法最初隻供內部使用，但在ASP.NET核心2.2中公開。</span><span class="sxs-lookup"><span data-stu-id="2455d-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2455d-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2455d-114">Recommended action</span></span>

<span data-ttu-id="2455d-115">不要使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="2455d-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="2455d-116">類別</span><span class="sxs-lookup"><span data-stu-id="2455d-116">Category</span></span>

<span data-ttu-id="2455d-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2455d-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2455d-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2455d-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901918"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="1da87-101">SignalR：已移除 HubConnection ResetSendPing 和 ResetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="1da87-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="1da87-102">`ResetSendPing`和 `ResetTimeout` 方法已從 SignalR API 中移除 `HubConnection` 。</span><span class="sxs-lookup"><span data-stu-id="1da87-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="1da87-103">這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中已公開。</span><span class="sxs-lookup"><span data-stu-id="1da87-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="1da87-104">從 ASP.NET Core 3.0 Preview 4 版開始，將無法使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="1da87-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="1da87-105">如需討論，請參閱 [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543)。</span><span class="sxs-lookup"><span data-stu-id="1da87-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1da87-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1da87-106">Version introduced</span></span>

<span data-ttu-id="1da87-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1da87-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1da87-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1da87-108">Old behavior</span></span>

<span data-ttu-id="1da87-109">Api 已可供使用。</span><span class="sxs-lookup"><span data-stu-id="1da87-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1da87-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="1da87-110">New behavior</span></span>

<span data-ttu-id="1da87-111">Api 已移除。</span><span class="sxs-lookup"><span data-stu-id="1da87-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1da87-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1da87-112">Reason for change</span></span>

<span data-ttu-id="1da87-113">這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中已公開。</span><span class="sxs-lookup"><span data-stu-id="1da87-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1da87-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1da87-114">Recommended action</span></span>

<span data-ttu-id="1da87-115">請勿使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="1da87-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="1da87-116">類別</span><span class="sxs-lookup"><span data-stu-id="1da87-116">Category</span></span>

<span data-ttu-id="1da87-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1da87-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1da87-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1da87-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

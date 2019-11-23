---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394022"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="1d4dc-101">SignalR：已移除 HubConnection ResetSendPing 和 ResetTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="1d4dc-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="1d4dc-102">`ResetSendPing` 和 `ResetTimeout` 方法已從 SignalR `HubConnection` API 移除。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="1d4dc-103">這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中公開。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="1d4dc-104">從 ASP.NET Core 3.0 Preview 4 版本開始，這些方法將無法使用。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="1d4dc-105">如需討論，請參閱[aspnet/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543)。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-105">For discussion, see [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1d4dc-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1d4dc-106">Version introduced</span></span>

<span data-ttu-id="1d4dc-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1d4dc-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1d4dc-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1d4dc-108">Old behavior</span></span>

<span data-ttu-id="1d4dc-109">Api 可供使用。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1d4dc-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="1d4dc-110">New behavior</span></span>

<span data-ttu-id="1d4dc-111">Api 已移除。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1d4dc-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1d4dc-112">Reason for change</span></span>

<span data-ttu-id="1d4dc-113">這些方法原本僅供內部使用，但在 ASP.NET Core 2.2 中公開。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1d4dc-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1d4dc-114">Recommended action</span></span>

<span data-ttu-id="1d4dc-115">請勿使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="1d4dc-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="1d4dc-116">類別</span><span class="sxs-lookup"><span data-stu-id="1d4dc-116">Category</span></span>

<span data-ttu-id="1d4dc-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1d4dc-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1d4dc-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1d4dc-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

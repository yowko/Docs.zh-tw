---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032380"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="6e65a-101">Kestrel：已移除並成為公用的傳輸抽象概念</span><span class="sxs-lookup"><span data-stu-id="6e65a-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="6e65a-102">在離開「pubternal」 Api 的過程中，Kestrel 傳輸層 Api 會公開為程式庫中的公用介面 `Microsoft.AspNetCore.Connections.Abstractions` 。</span><span class="sxs-lookup"><span data-stu-id="6e65a-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6e65a-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6e65a-103">Version introduced</span></span>

<span data-ttu-id="6e65a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="6e65a-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6e65a-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="6e65a-105">Old behavior</span></span>

- <span data-ttu-id="6e65a-106">程式庫中有提供傳輸相關的抽象概念 `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` 。</span><span class="sxs-lookup"><span data-stu-id="6e65a-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="6e65a-107">`ListenOptions.NoDelay`屬性為可用。</span><span class="sxs-lookup"><span data-stu-id="6e65a-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6e65a-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="6e65a-108">New behavior</span></span>

- <span data-ttu-id="6e65a-109">`IConnectionListener`介面是在程式庫中引進 `Microsoft.AspNetCore.Connections.Abstractions` ，以從程式庫公開最常使用的功能 `...Transport.Abstractions` 。</span><span class="sxs-lookup"><span data-stu-id="6e65a-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="6e65a-110">`NoDelay` (和) 的傳輸選項現在都有提供 `LibuvTransportOptions` `SocketTransportOptions` 。</span><span class="sxs-lookup"><span data-stu-id="6e65a-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="6e65a-111">`SchedulingMode` 無法再使用。</span><span class="sxs-lookup"><span data-stu-id="6e65a-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6e65a-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="6e65a-112">Reason for change</span></span>

<span data-ttu-id="6e65a-113">ASP.NET Core 3.0 已從 "pubternal" Api 中移除。</span><span class="sxs-lookup"><span data-stu-id="6e65a-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6e65a-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6e65a-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="6e65a-115">類別</span><span class="sxs-lookup"><span data-stu-id="6e65a-115">Category</span></span>

<span data-ttu-id="6e65a-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6e65a-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6e65a-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6e65a-117">Affected APIs</span></span>

<span data-ttu-id="6e65a-118">無</span><span class="sxs-lookup"><span data-stu-id="6e65a-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

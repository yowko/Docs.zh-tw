---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522674"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="bb3b5-101">Spa服務和節點服務不再回退到主控台記錄器</span><span class="sxs-lookup"><span data-stu-id="bb3b5-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="bb3b5-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>並且<xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType>不會顯示主控台日誌，除非配置了日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="bb3b5-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bb3b5-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="bb3b5-103">Version introduced</span></span>

<span data-ttu-id="bb3b5-104">3.0</span><span class="sxs-lookup"><span data-stu-id="bb3b5-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="bb3b5-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="bb3b5-105">Old behavior</span></span>

<span data-ttu-id="bb3b5-106">`Microsoft.AspNetCore.SpaServices`用於`Microsoft.AspNetCore.NodeServices`在未配置日誌記錄時自動創建主控台記錄器。</span><span class="sxs-lookup"><span data-stu-id="bb3b5-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="bb3b5-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="bb3b5-107">New behavior</span></span>

<span data-ttu-id="bb3b5-108">`Microsoft.AspNetCore.SpaServices`並且`Microsoft.AspNetCore.NodeServices`不會顯示主控台日誌，除非配置了日誌記錄。</span><span class="sxs-lookup"><span data-stu-id="bb3b5-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bb3b5-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="bb3b5-109">Reason for change</span></span>

<span data-ttu-id="bb3b5-110">需要與其他ASP.NET核心包實現日誌記錄的方式保持一致。</span><span class="sxs-lookup"><span data-stu-id="bb3b5-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bb3b5-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bb3b5-111">Recommended action</span></span>

<span data-ttu-id="bb3b5-112">如果需要舊行為，要配置主控台日誌記錄，請添加到`services.AddLogging(builder => builder.AddConsole())`方法。 `Setup.ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="bb3b5-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="bb3b5-113">類別</span><span class="sxs-lookup"><span data-stu-id="bb3b5-113">Category</span></span>

<span data-ttu-id="bb3b5-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bb3b5-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bb3b5-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bb3b5-115">Affected APIs</span></span>

<span data-ttu-id="bb3b5-116">None</span><span class="sxs-lookup"><span data-stu-id="bb3b5-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

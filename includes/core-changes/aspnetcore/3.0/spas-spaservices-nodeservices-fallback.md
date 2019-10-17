---
ms.openlocfilehash: 1017801346e65940e4dc075ef72f7a00d7e6bcd9
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394132"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="b9052-101">Spa： SpaServices 和 NodeServices 不再回到主控台記錄器</span><span class="sxs-lookup"><span data-stu-id="b9052-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="b9052-102">除非已設定記錄，否則 <xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> 和 <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> 不會顯示主控台記錄。</span><span class="sxs-lookup"><span data-stu-id="b9052-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b9052-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b9052-103">Version introduced</span></span>

<span data-ttu-id="b9052-104">3.0</span><span class="sxs-lookup"><span data-stu-id="b9052-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b9052-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b9052-105">Old behavior</span></span>

<span data-ttu-id="b9052-106">`Microsoft.AspNetCore.SpaServices` 和 `Microsoft.AspNetCore.NodeServices`，用於在未設定記錄時自動建立主控台記錄器。</span><span class="sxs-lookup"><span data-stu-id="b9052-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span> 

#### <a name="new-behavior"></a><span data-ttu-id="b9052-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="b9052-107">New behavior</span></span>

<span data-ttu-id="b9052-108">除非已設定記錄，否則 `Microsoft.AspNetCore.SpaServices` 和 `Microsoft.AspNetCore.NodeServices` 不會顯示主控台記錄。</span><span class="sxs-lookup"><span data-stu-id="b9052-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b9052-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b9052-109">Reason for change</span></span>

<span data-ttu-id="b9052-110">您必須配合其他 ASP.NET Core 封裝如何執行記錄。</span><span class="sxs-lookup"><span data-stu-id="b9052-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b9052-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b9052-111">Recommended action</span></span>

<span data-ttu-id="b9052-112">如果需要舊的行為，若要設定主控台記錄，請將 `services.AddLogging(builder => builder.AddConsole())` 新增至您的 @no__t 1 方法。</span><span class="sxs-lookup"><span data-stu-id="b9052-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="b9052-113">分類</span><span class="sxs-lookup"><span data-stu-id="b9052-113">Category</span></span>

<span data-ttu-id="b9052-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b9052-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b9052-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b9052-115">Affected APIs</span></span>

<span data-ttu-id="b9052-116">無</span><span class="sxs-lookup"><span data-stu-id="b9052-116">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

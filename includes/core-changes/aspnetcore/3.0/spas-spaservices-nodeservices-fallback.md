---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522674"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="23110-101">Spa： SpaServices 和 NodeServices 不會再切換回主控台記錄器</span><span class="sxs-lookup"><span data-stu-id="23110-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="23110-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType><xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType>除非已設定記錄，否則不會顯示主控台記錄。</span><span class="sxs-lookup"><span data-stu-id="23110-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="23110-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="23110-103">Version introduced</span></span>

<span data-ttu-id="23110-104">3.0</span><span class="sxs-lookup"><span data-stu-id="23110-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="23110-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="23110-105">Old behavior</span></span>

<span data-ttu-id="23110-106">`Microsoft.AspNetCore.SpaServices` 並且 `Microsoft.AspNetCore.NodeServices` 用來在未設定記錄時，自動建立主控台記錄器。</span><span class="sxs-lookup"><span data-stu-id="23110-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="23110-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="23110-107">New behavior</span></span>

<span data-ttu-id="23110-108">`Microsoft.AspNetCore.SpaServices``Microsoft.AspNetCore.NodeServices`除非已設定記錄，否則不會顯示主控台記錄。</span><span class="sxs-lookup"><span data-stu-id="23110-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="23110-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="23110-109">Reason for change</span></span>

<span data-ttu-id="23110-110">您需要與其他 ASP.NET Core 封裝如何執行記錄。</span><span class="sxs-lookup"><span data-stu-id="23110-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="23110-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="23110-111">Recommended action</span></span>

<span data-ttu-id="23110-112">如果需要舊的行為，若要設定主控台記錄，請在您的方法中新增 `services.AddLogging(builder => builder.AddConsole())` `Setup.ConfigureServices` 。</span><span class="sxs-lookup"><span data-stu-id="23110-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="23110-113">類別</span><span class="sxs-lookup"><span data-stu-id="23110-113">Category</span></span>

<span data-ttu-id="23110-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="23110-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23110-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="23110-115">Affected APIs</span></span>

<span data-ttu-id="23110-116">無</span><span class="sxs-lookup"><span data-stu-id="23110-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

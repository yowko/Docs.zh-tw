---
ms.openlocfilehash: c679cb2603d39f580203d9373d76481e904e6c1d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497246"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="05f10-101">分析 ASP.Net MVC4 應用程式可能會導致嚴重的執行引擎錯誤</span><span class="sxs-lookup"><span data-stu-id="05f10-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="05f10-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="05f10-102">Details</span></span>

<span data-ttu-id="05f10-103">使用 NGEN /Profile 組件的分析工具可能會在啟動時損毀已分析的 ASP.NET MVC4 應用程式，並顯示「嚴重的執行引擎例外狀況」</span><span class="sxs-lookup"><span data-stu-id="05f10-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="05f10-104">建議</span><span class="sxs-lookup"><span data-stu-id="05f10-104">Suggestion</span></span>

<span data-ttu-id="05f10-105">此問題在 .NET Framework 4.5.2 中已修正。</span><span class="sxs-lookup"><span data-stu-id="05f10-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="05f10-106">或者，分析工具時可能會藉由在其事件遮罩中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 來避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="05f10-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="05f10-107">名稱</span><span class="sxs-lookup"><span data-stu-id="05f10-107">Name</span></span>    | <span data-ttu-id="05f10-108">值</span><span class="sxs-lookup"><span data-stu-id="05f10-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="05f10-109">範圍</span><span class="sxs-lookup"><span data-stu-id="05f10-109">Scope</span></span>   |<span data-ttu-id="05f10-110">Edge</span><span class="sxs-lookup"><span data-stu-id="05f10-110">Edge</span></span>|
|<span data-ttu-id="05f10-111">版本</span><span class="sxs-lookup"><span data-stu-id="05f10-111">Version</span></span>|<span data-ttu-id="05f10-112">4.5</span><span class="sxs-lookup"><span data-stu-id="05f10-112">4.5</span></span>|
|<span data-ttu-id="05f10-113">類型</span><span class="sxs-lookup"><span data-stu-id="05f10-113">Type</span></span>|<span data-ttu-id="05f10-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="05f10-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="05f10-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="05f10-115">Affected APIs</span></span>

<span data-ttu-id="05f10-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="05f10-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

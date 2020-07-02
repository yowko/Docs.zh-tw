---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622033"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="6767a-101">分析 ASP.Net MVC4 應用程式可能會導致嚴重的執行引擎錯誤</span><span class="sxs-lookup"><span data-stu-id="6767a-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="6767a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6767a-102">Details</span></span>

<span data-ttu-id="6767a-103">使用 NGEN /Profile 組件的分析工具可能會在啟動時損毀已分析的 ASP.NET MVC4 應用程式，並顯示「嚴重的執行引擎例外狀況」</span><span class="sxs-lookup"><span data-stu-id="6767a-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6767a-104">建議</span><span class="sxs-lookup"><span data-stu-id="6767a-104">Suggestion</span></span>

<span data-ttu-id="6767a-105">此問題在 .NET Framework 4.5.2 中已修正。</span><span class="sxs-lookup"><span data-stu-id="6767a-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="6767a-106">或者，分析工具時可能會藉由在其事件遮罩中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 來避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="6767a-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="6767a-107">名稱</span><span class="sxs-lookup"><span data-stu-id="6767a-107">Name</span></span>    | <span data-ttu-id="6767a-108">值</span><span class="sxs-lookup"><span data-stu-id="6767a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6767a-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="6767a-109">Scope</span></span>   |<span data-ttu-id="6767a-110">Edge</span><span class="sxs-lookup"><span data-stu-id="6767a-110">Edge</span></span>|
|<span data-ttu-id="6767a-111">版本</span><span class="sxs-lookup"><span data-stu-id="6767a-111">Version</span></span>|<span data-ttu-id="6767a-112">4.5</span><span class="sxs-lookup"><span data-stu-id="6767a-112">4.5</span></span>|
|<span data-ttu-id="6767a-113">類型</span><span class="sxs-lookup"><span data-stu-id="6767a-113">Type</span></span>|<span data-ttu-id="6767a-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="6767a-114">Runtime</span></span>|

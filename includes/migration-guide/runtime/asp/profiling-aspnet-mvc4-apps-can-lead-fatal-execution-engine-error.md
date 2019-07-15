---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803221"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="654c1-101">分析 ASP.Net MVC4 應用程式可能會導致嚴重的執行引擎錯誤</span><span class="sxs-lookup"><span data-stu-id="654c1-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="654c1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="654c1-102">Details</span></span>|<span data-ttu-id="654c1-103">使用 NGEN /Profile 組件的分析工具可能會在啟動時損毀已分析的 ASP.NET MVC4 應用程式，並顯示「嚴重的執行引擎例外狀況」</span><span class="sxs-lookup"><span data-stu-id="654c1-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="654c1-104">建議</span><span class="sxs-lookup"><span data-stu-id="654c1-104">Suggestion</span></span>|<span data-ttu-id="654c1-105">此問題在 .NET Framework 4.5.2 中已修正。</span><span class="sxs-lookup"><span data-stu-id="654c1-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="654c1-106">或者，分析工具時可能會藉由在其事件遮罩中指定 <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> 來避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="654c1-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="654c1-107">範圍</span><span class="sxs-lookup"><span data-stu-id="654c1-107">Scope</span></span>|<span data-ttu-id="654c1-108">Edge</span><span class="sxs-lookup"><span data-stu-id="654c1-108">Edge</span></span>|
|<span data-ttu-id="654c1-109">版本</span><span class="sxs-lookup"><span data-stu-id="654c1-109">Version</span></span>|<span data-ttu-id="654c1-110">4.5</span><span class="sxs-lookup"><span data-stu-id="654c1-110">4.5</span></span>|
|<span data-ttu-id="654c1-111">類型</span><span class="sxs-lookup"><span data-stu-id="654c1-111">Type</span></span>|<span data-ttu-id="654c1-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="654c1-112">Runtime</span></span>|


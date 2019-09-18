---
title: 使用 Serviced 元件和全域組件快取
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4edc675e0348f06114b8162022f1d9420e0cec52
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053070"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="8533f-102">使用 Serviced 元件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="8533f-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="8533f-103">Serviced 元件 (受控碼 COM+ 元件) 都應該放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="8533f-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="8533f-104">在某些情況下，通用語言執行平台和 COM + 服務可以處理不在全域組件快取中的 Serviced 元件；但在其他案例中則不能。</span><span class="sxs-lookup"><span data-stu-id="8533f-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="8533f-105">下列案例可說明這種情況：</span><span class="sxs-lookup"><span data-stu-id="8533f-105">The following scenarios illustrate this:</span></span>  
  
- <span data-ttu-id="8533f-106">若是 COM+ 伺服器應用程式中的 Serviced 元件，由於 Dllhost.exe 的執行位置不在包含 Serviced 元件的相同目錄中，因此含有元件的組件必須位於全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="8533f-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
- <span data-ttu-id="8533f-107">若是 COM+ 程式庫應用程式中的 Serviced 元件，執行階段和 COM+ 服務可以搜尋目前的目錄，以解析含有元件的組件參考。</span><span class="sxs-lookup"><span data-stu-id="8533f-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="8533f-108">在這種情況下，組件就不需要位於全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="8533f-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
- <span data-ttu-id="8533f-109">若是 ASP.NET 應用程式中的 Serviced 元件，情況又不同。</span><span class="sxs-lookup"><span data-stu-id="8533f-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="8533f-110">如果您將包含 Serviced 元件的組件放置在應用程式基底的 bin 目錄中，並使用隨選的註冊，則系統會將組件陰影複製到下載快取，因為 ASP.NET 會使用執行階段的陰影功能。</span><span class="sxs-lookup"><span data-stu-id="8533f-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8533f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8533f-111">See also</span></span>

- [<span data-ttu-id="8533f-112">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="8533f-112">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="8533f-113">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="8533f-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)

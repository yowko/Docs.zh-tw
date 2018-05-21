---
title: 共用 Web 裝載的最佳化
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3c979477f0928c9c3d2a393042867c84df33ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="87bb5-102">共用 Web 裝載的最佳化</span><span class="sxs-lookup"><span data-stu-id="87bb5-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="87bb5-103">如果您是透過裝載數個小型 Web 站台所共用之伺服器的系統管理員，則可以將下列 `gcTrimCommitOnLowMemory` 設定加入 .NET 目錄中 Aspnet.config 檔案的 `runtime` 節點，以最佳化效能與增加站台的容量：</span><span class="sxs-lookup"><span data-stu-id="87bb5-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="87bb5-104">此設定僅建議針對共用 Web 裝載案例使用。</span><span class="sxs-lookup"><span data-stu-id="87bb5-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="87bb5-105">因為記憶體回收行程會保留供未來配置使用的記憶體，其認可空間可以超過嚴格需要的空間。</span><span class="sxs-lookup"><span data-stu-id="87bb5-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="87bb5-106">您可以減少這個空間，以容納系統記憶體負載過重的時間。</span><span class="sxs-lookup"><span data-stu-id="87bb5-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="87bb5-107">減少此認可空間會改善效能，並擴充容量以裝載更多站台。</span><span class="sxs-lookup"><span data-stu-id="87bb5-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="87bb5-108">當啟用 `gcTrimCommitOnLowMemory` 設定時，記憶體回收行程會評估系統記憶體負載，並在負載達到 90% 時進入調整模式。</span><span class="sxs-lookup"><span data-stu-id="87bb5-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="87bb5-109">它會維持調整模式，直到負載降至 85%。</span><span class="sxs-lookup"><span data-stu-id="87bb5-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="87bb5-110">當情況允許時，記憶體回收行程可以決定 `gcTrimCommitOnLowMemory` 設定不會協助目前的應用程式並忽略它。</span><span class="sxs-lookup"><span data-stu-id="87bb5-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87bb5-111">範例</span><span class="sxs-lookup"><span data-stu-id="87bb5-111">Example</span></span>  
 <span data-ttu-id="87bb5-112">下列 XML 片段會示範如何啟用 `gcTrimCommitOnLowMemory` 設定。</span><span class="sxs-lookup"><span data-stu-id="87bb5-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="87bb5-113">省略符號表示 `runtime` 節點中可能有的其他設定。</span><span class="sxs-lookup"><span data-stu-id="87bb5-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87bb5-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="87bb5-114">See Also</span></span>  
 [<span data-ttu-id="87bb5-115">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="87bb5-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)

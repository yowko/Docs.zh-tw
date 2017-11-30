---
title: "共用 Web 裝載的最佳化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="97f81-102">共用 Web 裝載的最佳化</span><span class="sxs-lookup"><span data-stu-id="97f81-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="97f81-103">如果您是由裝載數個小型 Web 站台所共用的伺服器管理員，可以最佳化效能並增加站台的容量，加入下列`gcTrimCommitOnLowMemory`設`runtime`Aspnet.config 檔案，在.NET 中的節點目錄：</span><span class="sxs-lookup"><span data-stu-id="97f81-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="97f81-104">這項設定被建議只針對共用 Web 裝載案例。</span><span class="sxs-lookup"><span data-stu-id="97f81-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="97f81-105">因為記憶體回收行程會保留供未來的配置的記憶體，認可的空間可以是多個嚴格的需要。</span><span class="sxs-lookup"><span data-stu-id="97f81-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="97f81-106">您可以減少這個空間來容納時間時的負載過重的系統記憶體。</span><span class="sxs-lookup"><span data-stu-id="97f81-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="97f81-107">減少認可的空間可改善效能，並展開裝載更多站台的容量。</span><span class="sxs-lookup"><span data-stu-id="97f81-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="97f81-108">當`gcTrimCommitOnLowMemory`設定時，記憶體回收行程評估系統的記憶體負載，並載入到達 90%時，會進入調整模式。</span><span class="sxs-lookup"><span data-stu-id="97f81-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="97f81-109">它會維護調整模式，直到負載降至 85%。</span><span class="sxs-lookup"><span data-stu-id="97f81-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="97f81-110">當情況允許時，記憶體回收行程可以決定，`gcTrimCommitOnLowMemory`設定不會說明目前的應用程式，並忽略它。</span><span class="sxs-lookup"><span data-stu-id="97f81-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f81-111">範例</span><span class="sxs-lookup"><span data-stu-id="97f81-111">Example</span></span>  
 <span data-ttu-id="97f81-112">下列 XML 片段會示範如何啟用`gcTrimCommitOnLowMemory`設定。</span><span class="sxs-lookup"><span data-stu-id="97f81-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="97f81-113">省略符號表示可能會在其他設定`runtime`節點。</span><span class="sxs-lookup"><span data-stu-id="97f81-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97f81-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97f81-114">See Also</span></span>  
 [<span data-ttu-id="97f81-115">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="97f81-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)

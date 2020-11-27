---
title: 組件定位
description: 請參閱目錄中 .NET 元件放置的指導方針 (例如，在全域組件快取中，或在應用程式的目錄或子目錄) 中。
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 15ff6edf5887062b0cce918b39beef6c9b618ca2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271548"
---
# <a name="assembly-placement"></a><span data-ttu-id="8e415-103">組件定位</span><span class="sxs-lookup"><span data-stu-id="8e415-103">Assembly Placement</span></span>

<span data-ttu-id="8e415-104">對於大部分 .NET Framework 應用程式，您可以將構成該應用程式的組件放置在應用程式的目錄、應用程式目錄的子目錄或全域組件快取 (如果該組件是共用的) 中。</span><span class="sxs-lookup"><span data-stu-id="8e415-104">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="8e415-105">您可以使用設定檔中的[ \<codeBase> 元素](../configure-apps/file-schema/runtime/codebase-element.md)，覆寫 common language runtime 尋找元件的位置。</span><span class="sxs-lookup"><span data-stu-id="8e415-105">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="8e415-106">如果元件沒有強式名稱，則使用[ \<codeBase> 元素](../configure-apps/file-schema/runtime/codebase-element.md)所指定的位置會限制為應用程式目錄或子目錄。</span><span class="sxs-lookup"><span data-stu-id="8e415-106">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="8e415-107">如果元件具有強式名稱，則[ \<codeBase> 元素](../configure-apps/file-schema/runtime/codebase-element.md)可以指定電腦或網路上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="8e415-107">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="8e415-108">使用 Unmanaged 程式碼或 COM Interop 應用程式時，可套用類似的規則來尋找組件：如果將會有多個應用程式共用這個組件，應該將它安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="8e415-108">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="8e415-109">配合 Unmanaged 程式碼使用的組件必須匯出為型別程式庫並且加以註冊。</span><span class="sxs-lookup"><span data-stu-id="8e415-109">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="8e415-110">COM Interop 所使用的組件必須在資料庫目錄 (Catalog) 中註冊，不過在某些狀況下這項註冊會自動進行。</span><span class="sxs-lookup"><span data-stu-id="8e415-110">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e415-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e415-111">See also</span></span>

- [<span data-ttu-id="8e415-112">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="8e415-112">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="8e415-113">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="8e415-113">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="8e415-114">與非受控程式碼交互操作</span><span class="sxs-lookup"><span data-stu-id="8e415-114">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="8e415-115">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="8e415-115">Assemblies in .NET</span></span>](index.md)

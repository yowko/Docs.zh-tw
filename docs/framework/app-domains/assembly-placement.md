---
title: 組件定位
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 829aa80169319b67a8cc5ee39fee9214cd4fcbce
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971632"
---
# <a name="assembly-placement"></a><span data-ttu-id="d0216-102">組件定位</span><span class="sxs-lookup"><span data-stu-id="d0216-102">Assembly Placement</span></span>
<span data-ttu-id="d0216-103">對於大部分 .NET Framework 應用程式，您可以將構成該應用程式的組件放置在應用程式的目錄、應用程式目錄的子目錄或全域組件快取 (如果該組件是共用的) 中。</span><span class="sxs-lookup"><span data-stu-id="d0216-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="d0216-104">您可以使用組態檔中的 [\<codeBase> 項目](../../framework/configure-apps/file-schema/runtime/codebase-element.md)來覆寫 Common Language Runtime 尋找組件的位置。</span><span class="sxs-lookup"><span data-stu-id="d0216-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="d0216-105">如果組件不具有強式名稱，就會將使用 [\<codeBase> 項目](../../framework/configure-apps/file-schema/runtime/codebase-element.md)所指定的位置限制為應用程式目錄或子目錄。</span><span class="sxs-lookup"><span data-stu-id="d0216-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="d0216-106">如果組件具有強式名稱，[\<codeBase> 項目](../../framework/configure-apps/file-schema/runtime/codebase-element.md)即可以指定電腦或網路上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="d0216-106">If the assembly has a strong name, the [\<codeBase> Element](../../framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="d0216-107">使用 Unmanaged 程式碼或 COM Interop 應用程式時，可套用類似的規則來尋找組件：如果將會有多個應用程式共用這個組件，應該將它安裝在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="d0216-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="d0216-108">配合 Unmanaged 程式碼使用的組件必須匯出為型別程式庫並且加以註冊。</span><span class="sxs-lookup"><span data-stu-id="d0216-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="d0216-109">COM Interop 所使用的組件必須在資料庫目錄 (Catalog) 中註冊，不過在某些狀況下這項註冊會自動進行。</span><span class="sxs-lookup"><span data-stu-id="d0216-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0216-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0216-110">See also</span></span>

- [<span data-ttu-id="d0216-111">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="d0216-111">How the Runtime Locates Assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="d0216-112">設定應用程式</span><span class="sxs-lookup"><span data-stu-id="d0216-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="d0216-113">與非受控程式碼交互操作</span><span class="sxs-lookup"><span data-stu-id="d0216-113">Interoperating with unmanaged code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="d0216-114">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="d0216-114">Assemblies in .NET</span></span>](index.md)

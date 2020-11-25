---
title: IAssemblyCache 介面
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
ms.openlocfilehash: df4f0ba018b55202c22cb90b22b927a9c426c4ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696852"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="596f3-102">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="596f3-102">IAssemblyCache Interface</span></span>

<span data-ttu-id="596f3-103">代表融合技術所使用的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="596f3-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="596f3-104">方法</span><span class="sxs-lookup"><span data-stu-id="596f3-104">Methods</span></span>  
  
|<span data-ttu-id="596f3-105">方法</span><span class="sxs-lookup"><span data-stu-id="596f3-105">Method</span></span>|<span data-ttu-id="596f3-106">描述</span><span class="sxs-lookup"><span data-stu-id="596f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="596f3-107">CreateAssemblyCacheItem 方法</span><span class="sxs-lookup"><span data-stu-id="596f3-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="596f3-108">取得新 [IAssemblyCacheItem](iassemblycacheitem-interface.md)的參考。</span><span class="sxs-lookup"><span data-stu-id="596f3-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="596f3-109">CreateAssemblyScavenger 方法</span><span class="sxs-lookup"><span data-stu-id="596f3-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="596f3-110">保留供融合技術內部使用。</span><span class="sxs-lookup"><span data-stu-id="596f3-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="596f3-111">InstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="596f3-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="596f3-112">在全域組件快取中安裝指定的元件。</span><span class="sxs-lookup"><span data-stu-id="596f3-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="596f3-113">QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="596f3-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="596f3-114">取得所要求有關指定元件的資料。</span><span class="sxs-lookup"><span data-stu-id="596f3-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="596f3-115">UninstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="596f3-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="596f3-116">從全域組件快取卸載指定的元件。</span><span class="sxs-lookup"><span data-stu-id="596f3-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="596f3-117">需求</span><span class="sxs-lookup"><span data-stu-id="596f3-117">Requirements</span></span>  

 <span data-ttu-id="596f3-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="596f3-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="596f3-119">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="596f3-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="596f3-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="596f3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596f3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="596f3-121">See also</span></span>

- [<span data-ttu-id="596f3-122">融合介面</span><span class="sxs-lookup"><span data-stu-id="596f3-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="596f3-123">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="596f3-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)

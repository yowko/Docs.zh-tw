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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dab5fe941fce3c23ba718906b29c80c6d257c2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796776"
---
# <a name="iassemblycache-interface"></a><span data-ttu-id="bc157-102">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="bc157-102">IAssemblyCache Interface</span></span>
<span data-ttu-id="bc157-103">代表融合技術所使用的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="bc157-103">Represents the global assembly cache for use by the fusion technology.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bc157-104">方法</span><span class="sxs-lookup"><span data-stu-id="bc157-104">Methods</span></span>  
  
|<span data-ttu-id="bc157-105">方法</span><span class="sxs-lookup"><span data-stu-id="bc157-105">Method</span></span>|<span data-ttu-id="bc157-106">說明</span><span class="sxs-lookup"><span data-stu-id="bc157-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bc157-107">CreateAssemblyCacheItem 方法</span><span class="sxs-lookup"><span data-stu-id="bc157-107">CreateAssemblyCacheItem Method</span></span>](iassemblycache-createassemblycacheitem-method.md)|<span data-ttu-id="bc157-108">取得新[IAssemblyCacheItem](iassemblycacheitem-interface.md)的參考。</span><span class="sxs-lookup"><span data-stu-id="bc157-108">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md).</span></span>|  
|[<span data-ttu-id="bc157-109">CreateAssemblyScavenger 方法</span><span class="sxs-lookup"><span data-stu-id="bc157-109">CreateAssemblyScavenger Method</span></span>](iassemblycache-createassemblyscavenger-method.md)|<span data-ttu-id="bc157-110">保留供融合技術內部使用。</span><span class="sxs-lookup"><span data-stu-id="bc157-110">Reserved for internal use by the fusion technology.</span></span>|  
|[<span data-ttu-id="bc157-111">InstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="bc157-111">InstallAssembly Method</span></span>](iassemblycache-installassembly-method.md)|<span data-ttu-id="bc157-112">在全域組件快取中安裝指定的元件。</span><span class="sxs-lookup"><span data-stu-id="bc157-112">Installs the specified assembly in the global assembly cache.</span></span>|  
|[<span data-ttu-id="bc157-113">QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="bc157-113">QueryAssemblyInfo Method</span></span>](iassemblycache-queryassemblyinfo-method.md)|<span data-ttu-id="bc157-114">取得指定元件的要求資料。</span><span class="sxs-lookup"><span data-stu-id="bc157-114">Gets the requested data about the specified assembly.</span></span>|  
|[<span data-ttu-id="bc157-115">UninstallAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="bc157-115">UninstallAssembly Method</span></span>](iassemblycache-uninstallassembly-method.md)|<span data-ttu-id="bc157-116">從全域組件快取卸載指定的元件。</span><span class="sxs-lookup"><span data-stu-id="bc157-116">Uninstalls the specified assembly from the global assembly cache.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc157-117">需求</span><span class="sxs-lookup"><span data-stu-id="bc157-117">Requirements</span></span>  
 <span data-ttu-id="bc157-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc157-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc157-119">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="bc157-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bc157-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc157-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc157-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc157-121">See also</span></span>

- [<span data-ttu-id="bc157-122">融合介面</span><span class="sxs-lookup"><span data-stu-id="bc157-122">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="bc157-123">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="bc157-123">Global Assembly Cache</span></span>](../../app-domains/gac.md)

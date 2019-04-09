---
title: IAssemblyCacheItem 介面
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fba17a2ffad9220acdbc79726efe0d3d4184978a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188548"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="3f575-102">IAssemblyCacheItem 介面</span><span class="sxs-lookup"><span data-stu-id="3f575-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="3f575-103">表示在全域組件快取中的單一組件。</span><span class="sxs-lookup"><span data-stu-id="3f575-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f575-104">方法</span><span class="sxs-lookup"><span data-stu-id="3f575-104">Methods</span></span>  
  
|<span data-ttu-id="3f575-105">方法</span><span class="sxs-lookup"><span data-stu-id="3f575-105">Method</span></span>|<span data-ttu-id="3f575-106">描述</span><span class="sxs-lookup"><span data-stu-id="3f575-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f575-107">AbortItem 方法</span><span class="sxs-lookup"><span data-stu-id="3f575-107">AbortItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="3f575-108">允許在全域組件快取中的組件，在發行之前執行清除作業。</span><span class="sxs-lookup"><span data-stu-id="3f575-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="3f575-109">Commit 方法</span><span class="sxs-lookup"><span data-stu-id="3f575-109">Commit Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-commit-method.md)|<span data-ttu-id="3f575-110">認可記憶體的快取的組件參考。</span><span class="sxs-lookup"><span data-stu-id="3f575-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="3f575-111">CreateStream 方法</span><span class="sxs-lookup"><span data-stu-id="3f575-111">CreateStream Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-createstream-method.md)|<span data-ttu-id="3f575-112">建立具有指定的名稱和格式的資料流。</span><span class="sxs-lookup"><span data-stu-id="3f575-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f575-113">需求</span><span class="sxs-lookup"><span data-stu-id="3f575-113">Requirements</span></span>  
 <span data-ttu-id="3f575-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f575-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f575-115">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3f575-115">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="3f575-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3f575-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f575-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f575-117">See also</span></span>

- [<span data-ttu-id="3f575-118">融合介面</span><span class="sxs-lookup"><span data-stu-id="3f575-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="3f575-119">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="3f575-119">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="3f575-120">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="3f575-120">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)

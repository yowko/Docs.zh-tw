---
title: "ICorProfilerInfo7 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a85bf82a01f431e42a5714eeb54e17a34314534
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="1d2d5-102">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="1d2d5-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="1d2d5-103">[受到 [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="1d2d5-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="1d2d5-104">子類別[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) ，提供方法，以套用新定義模組的中繼資料與可存取的記憶體中的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="1d2d5-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d2d5-105">方法</span><span class="sxs-lookup"><span data-stu-id="1d2d5-105">Methods</span></span>  
  
|<span data-ttu-id="1d2d5-106">方法</span><span class="sxs-lookup"><span data-stu-id="1d2d5-106">Method</span></span>|<span data-ttu-id="1d2d5-107">說明</span><span class="sxs-lookup"><span data-stu-id="1d2d5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d2d5-108">ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="1d2d5-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="1d2d5-109">適用於新所定義的中繼資料`IMetadataEmit::Define*`方法，以指定的模組。</span><span class="sxs-lookup"><span data-stu-id="1d2d5-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="1d2d5-110">GetInMemorySymbolsLength 方法</span><span class="sxs-lookup"><span data-stu-id="1d2d5-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="1d2d5-111">傳回的記憶體中的符號資料流的長度。</span><span class="sxs-lookup"><span data-stu-id="1d2d5-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="1d2d5-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="1d2d5-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="1d2d5-113">從記憶體中的符號資料流讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="1d2d5-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d2d5-114">需求</span><span class="sxs-lookup"><span data-stu-id="1d2d5-114">Requirements</span></span>  
 <span data-ttu-id="1d2d5-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2d5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d2d5-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1d2d5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1d2d5-117">**.NET framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d2d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2d5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d2d5-118">See Also</span></span>  
 [<span data-ttu-id="1d2d5-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="1d2d5-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

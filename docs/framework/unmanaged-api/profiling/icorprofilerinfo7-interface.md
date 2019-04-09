---
title: ICorProfilerInfo7 介面
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134841"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="5c631-102">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="5c631-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="5c631-103">[受到 [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 和更新版本的支援]</span><span class="sxs-lookup"><span data-stu-id="5c631-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="5c631-104">子類別[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)提供方法，以套用新定義模組的中繼資料，並提供存取記憶體中的符號資料流。</span><span class="sxs-lookup"><span data-stu-id="5c631-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c631-105">方法</span><span class="sxs-lookup"><span data-stu-id="5c631-105">Methods</span></span>  
  
|<span data-ttu-id="5c631-106">方法</span><span class="sxs-lookup"><span data-stu-id="5c631-106">Method</span></span>|<span data-ttu-id="5c631-107">描述</span><span class="sxs-lookup"><span data-stu-id="5c631-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c631-108">ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="5c631-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="5c631-109">適用於新所定義的中繼資料`IMetadataEmit::Define*`方法，以指定的模組。</span><span class="sxs-lookup"><span data-stu-id="5c631-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="5c631-110">GetInMemorySymbolsLength 方法</span><span class="sxs-lookup"><span data-stu-id="5c631-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="5c631-111">傳回記憶體中的符號資料流的長度。</span><span class="sxs-lookup"><span data-stu-id="5c631-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="5c631-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="5c631-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="5c631-113">從記憶體中的符號資料流讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="5c631-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c631-114">需求</span><span class="sxs-lookup"><span data-stu-id="5c631-114">Requirements</span></span>  
 <span data-ttu-id="5c631-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c631-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c631-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c631-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="5c631-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5c631-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5c631-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c631-118">See also</span></span>

- [<span data-ttu-id="5c631-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="5c631-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

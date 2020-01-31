---
title: ICorProfilerInfo7 介面
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861745"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="596a0-102">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="596a0-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="596a0-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="596a0-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="596a0-104">[ICorProfilerInfo6](icorprofilerinfo6-interface.md)的子類別，提供方法來將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。</span><span class="sxs-lookup"><span data-stu-id="596a0-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="596a0-105">方法</span><span class="sxs-lookup"><span data-stu-id="596a0-105">Methods</span></span>  
  
|<span data-ttu-id="596a0-106">方法</span><span class="sxs-lookup"><span data-stu-id="596a0-106">Method</span></span>|<span data-ttu-id="596a0-107">描述</span><span class="sxs-lookup"><span data-stu-id="596a0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="596a0-108">ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="596a0-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="596a0-109">將 `IMetadataEmit::Define*` 方法新定義的中繼資料套用至指定的模組。</span><span class="sxs-lookup"><span data-stu-id="596a0-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="596a0-110">GetInMemorySymbolsLength 方法</span><span class="sxs-lookup"><span data-stu-id="596a0-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="596a0-111">傳回記憶體中符號資料流程的長度。</span><span class="sxs-lookup"><span data-stu-id="596a0-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="596a0-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="596a0-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="596a0-113">從記憶體中的符號資料流程讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="596a0-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="596a0-114">需求</span><span class="sxs-lookup"><span data-stu-id="596a0-114">Requirements</span></span>  
 <span data-ttu-id="596a0-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="596a0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="596a0-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="596a0-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="596a0-117">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="596a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596a0-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="596a0-118">See also</span></span>

- [<span data-ttu-id="596a0-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="596a0-119">Profiling Interfaces</span></span>](profiling-interfaces.md)

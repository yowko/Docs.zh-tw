---
title: ICorProfilerInfo7 介面
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495485"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="32bf3-102">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="32bf3-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="32bf3-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="32bf3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="32bf3-104">[ICorProfilerInfo6](icorprofilerinfo6-interface.md)的子類別，提供方法來將新定義的中繼資料套用至模組，並提供記憶體內部符號資料流程的存取權。</span><span class="sxs-lookup"><span data-stu-id="32bf3-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="32bf3-105">方法</span><span class="sxs-lookup"><span data-stu-id="32bf3-105">Methods</span></span>  
  
|<span data-ttu-id="32bf3-106">方法</span><span class="sxs-lookup"><span data-stu-id="32bf3-106">Method</span></span>|<span data-ttu-id="32bf3-107">描述</span><span class="sxs-lookup"><span data-stu-id="32bf3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="32bf3-108">ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="32bf3-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="32bf3-109">將方法新定義的中繼資料套用 `IMetadataEmit::Define*` 至指定的模組。</span><span class="sxs-lookup"><span data-stu-id="32bf3-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="32bf3-110">GetInMemorySymbolsLength 方法</span><span class="sxs-lookup"><span data-stu-id="32bf3-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="32bf3-111">傳回記憶體中符號資料流程的長度。</span><span class="sxs-lookup"><span data-stu-id="32bf3-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="32bf3-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="32bf3-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="32bf3-113">從記憶體中的符號資料流程讀取位元組。</span><span class="sxs-lookup"><span data-stu-id="32bf3-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32bf3-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="32bf3-114">Requirements</span></span>  
 <span data-ttu-id="32bf3-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32bf3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bf3-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32bf3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32bf3-117">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bf3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bf3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32bf3-118">See also</span></span>

- [<span data-ttu-id="32bf3-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="32bf3-119">Profiling Interfaces</span></span>](profiling-interfaces.md)

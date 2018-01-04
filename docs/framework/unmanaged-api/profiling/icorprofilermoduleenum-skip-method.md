---
title: "ICorProfilerModuleEnum::Skip 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb6d12af329b214c78866ea352d1817afe0fa718
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="74111-102">ICorProfilerModuleEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="74111-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="74111-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="74111-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74111-104">語法</span><span class="sxs-lookup"><span data-stu-id="74111-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74111-105">參數</span><span class="sxs-lookup"><span data-stu-id="74111-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="74111-106">[in]要略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="74111-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74111-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="74111-107">Return Value</span></span>  
 <span data-ttu-id="74111-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="74111-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="74111-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="74111-109">HRESULT</span></span>|<span data-ttu-id="74111-110">描述</span><span class="sxs-lookup"><span data-stu-id="74111-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="74111-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="74111-111">S_OK</span></span>|<span data-ttu-id="74111-112">`celt`略過項目。</span><span class="sxs-lookup"><span data-stu-id="74111-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="74111-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="74111-113">S_FALSE</span></span>|<span data-ttu-id="74111-114">少於`celt`項目已略過，表示已沒有多個項目。</span><span class="sxs-lookup"><span data-stu-id="74111-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74111-115">備註</span><span class="sxs-lookup"><span data-stu-id="74111-115">Remarks</span></span>  
 <span data-ttu-id="74111-116">這個列舉值的資料指標的新位置時 （目前的位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="74111-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74111-117">需求</span><span class="sxs-lookup"><span data-stu-id="74111-117">Requirements</span></span>  
 <span data-ttu-id="74111-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74111-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74111-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74111-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74111-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74111-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74111-121">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74111-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74111-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="74111-122">See Also</span></span>  
 [<span data-ttu-id="74111-123">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="74111-123">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="74111-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="74111-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

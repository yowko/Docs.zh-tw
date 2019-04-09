---
title: ICorProfilerThreadEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cce96e8c6d046beba9e45c7121bf68444fd51c95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173338"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="332d6-102">ICorProfilerThreadEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="332d6-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="332d6-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="332d6-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="332d6-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="332d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="332d6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="332d6-106">[in]略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="332d6-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="332d6-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="332d6-107">Return Value</span></span>  
 <span data-ttu-id="332d6-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="332d6-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="332d6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="332d6-109">HRESULT</span></span>|<span data-ttu-id="332d6-110">描述</span><span class="sxs-lookup"><span data-stu-id="332d6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="332d6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="332d6-111">S_OK</span></span>|`celt` <span data-ttu-id="332d6-112">已略過項目。</span><span class="sxs-lookup"><span data-stu-id="332d6-112">elements were skipped.</span></span>|  
|<span data-ttu-id="332d6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="332d6-113">S_FALSE</span></span>|<span data-ttu-id="332d6-114">少於`celt`項目已略過，這表示為沒有多個項目。</span><span class="sxs-lookup"><span data-stu-id="332d6-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="332d6-115">備註</span><span class="sxs-lookup"><span data-stu-id="332d6-115">Remarks</span></span>  
 <span data-ttu-id="332d6-116">此列舉值的資料指標的新位置是 （目前的位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="332d6-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332d6-117">需求</span><span class="sxs-lookup"><span data-stu-id="332d6-117">Requirements</span></span>  
 <span data-ttu-id="332d6-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="332d6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="332d6-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="332d6-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="332d6-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="332d6-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="332d6-121">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="332d6-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="332d6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="332d6-122">See also</span></span>

- [<span data-ttu-id="332d6-123">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="332d6-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="332d6-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="332d6-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

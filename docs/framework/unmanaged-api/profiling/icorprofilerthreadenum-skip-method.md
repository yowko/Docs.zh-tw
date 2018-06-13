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
ms.openlocfilehash: af6aab2483f0e92dc20936fe2b01e12590d99ca7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455366"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="c9845-102">ICorProfilerThreadEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="c9845-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="c9845-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="c9845-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9845-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9845-104">Syntax</span></span>  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9845-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9845-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c9845-106">[in]要略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="c9845-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9845-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9845-107">Return Value</span></span>  
 <span data-ttu-id="c9845-108">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c9845-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c9845-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9845-109">HRESULT</span></span>|<span data-ttu-id="c9845-110">描述</span><span class="sxs-lookup"><span data-stu-id="c9845-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9845-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9845-111">S_OK</span></span>|<span data-ttu-id="c9845-112">`celt` 略過項目。</span><span class="sxs-lookup"><span data-stu-id="c9845-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="c9845-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c9845-113">S_FALSE</span></span>|<span data-ttu-id="c9845-114">少於`celt`項目已略過，表示已沒有多個項目。</span><span class="sxs-lookup"><span data-stu-id="c9845-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9845-115">備註</span><span class="sxs-lookup"><span data-stu-id="c9845-115">Remarks</span></span>  
 <span data-ttu-id="c9845-116">這個列舉值的資料指標的新位置時 （目前的位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="c9845-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9845-117">需求</span><span class="sxs-lookup"><span data-stu-id="c9845-117">Requirements</span></span>  
 <span data-ttu-id="c9845-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9845-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9845-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c9845-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c9845-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9845-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9845-121">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9845-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9845-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9845-122">See Also</span></span>  
 [<span data-ttu-id="c9845-123">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="c9845-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="c9845-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="c9845-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

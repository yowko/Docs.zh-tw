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
ms.openlocfilehash: 2c394c2b17404351bd0813ab1eb21230a1edd9de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781099"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="90af0-102">ICorProfilerThreadEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="90af0-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="90af0-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="90af0-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90af0-104">語法</span><span class="sxs-lookup"><span data-stu-id="90af0-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90af0-105">參數</span><span class="sxs-lookup"><span data-stu-id="90af0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="90af0-106">[in]略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="90af0-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90af0-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="90af0-107">Return Value</span></span>  
 <span data-ttu-id="90af0-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="90af0-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90af0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90af0-109">HRESULT</span></span>|<span data-ttu-id="90af0-110">描述</span><span class="sxs-lookup"><span data-stu-id="90af0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90af0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="90af0-111">S_OK</span></span>|<span data-ttu-id="90af0-112">`celt` 已略過項目。</span><span class="sxs-lookup"><span data-stu-id="90af0-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="90af0-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="90af0-113">S_FALSE</span></span>|<span data-ttu-id="90af0-114">少於`celt`項目已略過，這表示為沒有多個項目。</span><span class="sxs-lookup"><span data-stu-id="90af0-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90af0-115">備註</span><span class="sxs-lookup"><span data-stu-id="90af0-115">Remarks</span></span>  
 <span data-ttu-id="90af0-116">此列舉值的資料指標的新位置是 （目前的位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="90af0-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90af0-117">需求</span><span class="sxs-lookup"><span data-stu-id="90af0-117">Requirements</span></span>  
 <span data-ttu-id="90af0-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90af0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90af0-119">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90af0-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90af0-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90af0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90af0-121">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90af0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90af0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90af0-122">See also</span></span>

- [<span data-ttu-id="90af0-123">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="90af0-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="90af0-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="90af0-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

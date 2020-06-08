---
title: ICorProfilerModuleEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Skip method [.NET Framework profiling]
ms.assetid: 8dc29c6a-e2ba-41d8-a1e0-0fdd21421e0b
topic_type:
- apiref
ms.openlocfilehash: b48b782b7c8be35bfb815d72758f0bc316fb2114
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494718"
---
# <a name="icorprofilermoduleenumskip-method"></a><span data-ttu-id="f658c-102">ICorProfilerModuleEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="f658c-102">ICorProfilerModuleEnum::Skip Method</span></span>
<span data-ttu-id="f658c-103">將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。</span><span class="sxs-lookup"><span data-stu-id="f658c-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f658c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f658c-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f658c-105">參數</span><span class="sxs-lookup"><span data-stu-id="f658c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f658c-106">在要略過的元素數目。</span><span class="sxs-lookup"><span data-stu-id="f658c-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f658c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="f658c-107">Return Value</span></span>  
 <span data-ttu-id="f658c-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="f658c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f658c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f658c-109">HRESULT</span></span>|<span data-ttu-id="f658c-110">說明</span><span class="sxs-lookup"><span data-stu-id="f658c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f658c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f658c-111">S_OK</span></span>|<span data-ttu-id="f658c-112">`celt`已略過元素。</span><span class="sxs-lookup"><span data-stu-id="f658c-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="f658c-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f658c-113">S_FALSE</span></span>|<span data-ttu-id="f658c-114">略過少於個專案 `celt` ，這表示沒有更多元素。</span><span class="sxs-lookup"><span data-stu-id="f658c-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f658c-115">備註</span><span class="sxs-lookup"><span data-stu-id="f658c-115">Remarks</span></span>  
 <span data-ttu-id="f658c-116">這個列舉值的資料指標的新位置是（目前的位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="f658c-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f658c-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="f658c-117">Requirements</span></span>  
 <span data-ttu-id="f658c-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f658c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f658c-119">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f658c-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f658c-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f658c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f658c-121">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f658c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f658c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f658c-122">See also</span></span>

- [<span data-ttu-id="f658c-123">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f658c-123">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="f658c-124">分析介面</span><span class="sxs-lookup"><span data-stu-id="f658c-124">Profiling Interfaces</span></span>](profiling-interfaces.md)

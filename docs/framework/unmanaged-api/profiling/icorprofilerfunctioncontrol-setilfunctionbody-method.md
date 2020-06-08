---
title: ICorProfilerFunctionControl::SetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
ms.openlocfilehash: a6b24fd59a183a4a59b117663772417d55cc67db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503132"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="1c6a1-102">ICorProfilerFunctionControl::SetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="1c6a1-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="1c6a1-103">取代方法的 Common Intermediate Language (CIL) 主體。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c6a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c6a1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c6a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c6a1-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="1c6a1-106">[in] 新 CIL 的大小總計，包括主體後面的標頭和任何結構。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="1c6a1-107">[in] 新 CIL 標頭的指標。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c6a1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1c6a1-108">Return Value</span></span>  
 <span data-ttu-id="1c6a1-109">這個方法會傳回下列特定的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="1c6a1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c6a1-110">HRESULT</span></span>|<span data-ttu-id="1c6a1-111">說明</span><span class="sxs-lookup"><span data-stu-id="1c6a1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c6a1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c6a1-112">S_OK</span></span>|<span data-ttu-id="1c6a1-113">取代成功。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c6a1-114">備註</span><span class="sxs-lookup"><span data-stu-id="1c6a1-114">Remarks</span></span>  
 <span data-ttu-id="1c6a1-115">不同于[ICorProfilerInfo：： SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)方法， `SetILFunctionBody` 方法會管理新的 CIL 主體所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="1c6a1-116">這表示分析工具所提供的 CIL 主體不需要使用[IMethodMalloc](imethodmalloc-interface.md)介面來配置，或在特定範圍內配置。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="1c6a1-117">它可以配置於任何堆積上。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-117">It can be allocated on any heap.</span></span> <span data-ttu-id="1c6a1-118">分析工具可以在傳回之後釋放用於其 CIL 主體的記憶體 `SetILFunctionBody` 。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c6a1-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="1c6a1-119">Requirements</span></span>  
 <span data-ttu-id="1c6a1-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c6a1-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c6a1-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c6a1-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c6a1-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c6a1-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c6a1-123">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c6a1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c6a1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c6a1-124">See also</span></span>

- [<span data-ttu-id="1c6a1-125">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="1c6a1-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)

---
title: ICorProfilerInfo3::GetFunctionEnter3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164823"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="b4eeb-102">ICorProfilerInfo3::GetFunctionEnter3Info 方法</span><span class="sxs-lookup"><span data-stu-id="b4eeb-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="b4eeb-103">提供給分析工具所報告的函式之堆疊框架和引數資訊[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="b4eeb-104">只能在 `FunctionEnter3WithInfo` 回呼期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4eeb-105">語法</span><span class="sxs-lookup"><span data-stu-id="b4eeb-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4eeb-106">參數</span><span class="sxs-lookup"><span data-stu-id="b4eeb-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b4eeb-107">[in] 正在輸入之函式的 `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b4eeb-108">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b4eeb-109">分析工具應該提供相同`eltInfo`它是給定[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b4eeb-110">[out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b4eeb-111">此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionEnter3Info` 方法的 `FunctionEnter3WithInfo` 回呼中有效。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="b4eeb-112">[in、 out]大小總計，以位元組為單位的指標的[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)結構 (再加上任何額外[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) 所指向之引數範圍的結構`pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="b4eeb-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="b4eeb-113">如果指定的大小不足，會傳回 ERROR_INSUFFICIENT_BUFFER，且預期大小會儲存在 `pcbArgumentInfo`。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="b4eeb-114">若要呼叫 `GetFunctionEnter3Info` 以擷取預期的 `*pcbArgumentInfo` 值，請設定 `*pcbArgumentInfo`= 0 和 `pArgumentInfo`= NULL。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="b4eeb-115">[out]指標[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)結構，描述在記憶體中左到右的順序的函式的引數的位置。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4eeb-116">備註</span><span class="sxs-lookup"><span data-stu-id="b4eeb-116">Remarks</span></span>  
 <span data-ttu-id="b4eeb-117">程式碼剖析工具必須配置足夠的空間供檢查中之函式的 `COR_PRF_FUNCTION_ARGUMENT_INFO` 結構使用，且必須在 `pcbArgumentInfo` 參數指出大小。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4eeb-118">需求</span><span class="sxs-lookup"><span data-stu-id="b4eeb-118">Requirements</span></span>  
 <span data-ttu-id="b4eeb-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4eeb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4eeb-120">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4eeb-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4eeb-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4eeb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4eeb-122">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4eeb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4eeb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4eeb-123">See also</span></span>

- [<span data-ttu-id="b4eeb-124">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4eeb-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b4eeb-125">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4eeb-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="b4eeb-126">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b4eeb-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b4eeb-127">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="b4eeb-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b4eeb-128">分析介面</span><span class="sxs-lookup"><span data-stu-id="b4eeb-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b4eeb-129">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="b4eeb-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

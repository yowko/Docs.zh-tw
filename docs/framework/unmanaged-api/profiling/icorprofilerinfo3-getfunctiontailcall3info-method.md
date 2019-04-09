---
title: ICorProfilerInfo3::GetFunctionTailcall3Info 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40e518e3cf5967d2b0a7eda8c7b58ec0f918e219
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187423"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="f5428-102">ICorProfilerInfo3::GetFunctionTailcall3Info 方法</span><span class="sxs-lookup"><span data-stu-id="f5428-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="f5428-103">提供給分析工具所報告的函式的堆疊框架[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f5428-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="f5428-104">只能在 `FunctionTailcall3WithInfo` 回呼期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f5428-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5428-105">語法</span><span class="sxs-lookup"><span data-stu-id="f5428-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5428-106">參數</span><span class="sxs-lookup"><span data-stu-id="f5428-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f5428-107">[in]`FunctionID`函式傳回。</span><span class="sxs-lookup"><span data-stu-id="f5428-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="f5428-108">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f5428-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f5428-109">分析工具應該提供相同`eltInfo`，已指定用來藉由分析工具`FunctionTailcall3WithInfo`函式。</span><span class="sxs-lookup"><span data-stu-id="f5428-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="f5428-110">[out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f5428-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="f5428-111">此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionTailcall3Info` 方法的 `FunctionTailcall3WithInfo` 回呼中有效。</span><span class="sxs-lookup"><span data-stu-id="f5428-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5428-112">備註</span><span class="sxs-lookup"><span data-stu-id="f5428-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5428-113">需求</span><span class="sxs-lookup"><span data-stu-id="f5428-113">Requirements</span></span>  
 <span data-ttu-id="f5428-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5428-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5428-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5428-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5428-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5428-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f5428-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="f5428-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5428-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5428-118">See also</span></span>

- [<span data-ttu-id="f5428-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f5428-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="f5428-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f5428-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="f5428-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f5428-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="f5428-122">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="f5428-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f5428-123">分析介面</span><span class="sxs-lookup"><span data-stu-id="f5428-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f5428-124">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="f5428-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

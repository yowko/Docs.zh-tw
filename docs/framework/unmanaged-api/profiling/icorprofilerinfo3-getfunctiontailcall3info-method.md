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
ms.openlocfilehash: add89fe81fccbd5e6f5ad5d27f0ab3ace489963e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868521"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="34495-102">ICorProfilerInfo3::GetFunctionTailcall3Info 方法</span><span class="sxs-lookup"><span data-stu-id="34495-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="34495-103">提供[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)函式向分析工具報告之函式的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="34495-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="34495-104">只能在 `FunctionTailcall3WithInfo` 回呼期間呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="34495-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34495-105">語法</span><span class="sxs-lookup"><span data-stu-id="34495-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34495-106">參數</span><span class="sxs-lookup"><span data-stu-id="34495-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="34495-107">在傳回之函數的 `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="34495-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="34495-108">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="34495-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="34495-109">分析工具應該提供由 `FunctionTailcall3WithInfo` 函式指定給 profiler 的相同 `eltInfo`。</span><span class="sxs-lookup"><span data-stu-id="34495-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="34495-110">[out] 代表特定堆疊框架之泛型資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="34495-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="34495-111">此控制代碼只有在程式碼剖析工具呼叫 `GetFunctionTailcall3Info` 方法的 `FunctionTailcall3WithInfo` 回呼中有效。</span><span class="sxs-lookup"><span data-stu-id="34495-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34495-112">備註</span><span class="sxs-lookup"><span data-stu-id="34495-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34495-113">需求</span><span class="sxs-lookup"><span data-stu-id="34495-113">Requirements</span></span>  
 <span data-ttu-id="34495-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34495-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34495-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34495-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34495-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34495-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34495-117">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34495-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34495-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="34495-118">See also</span></span>

- [<span data-ttu-id="34495-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="34495-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="34495-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="34495-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="34495-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="34495-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="34495-122">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="34495-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="34495-123">分析介面</span><span class="sxs-lookup"><span data-stu-id="34495-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="34495-124">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="34495-124">Profiling</span></span>](index.md)

---
title: FunctionIDMapper2 函式
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a236dcae29d00afe3b72dce8f81d657fb4fac28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082499"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="4f3cb-102">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="4f3cb-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="4f3cb-103">通知分析工具的函式指定的識別項可能會重新對應至替代識別碼，以用於[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，和[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)，或[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)， [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)，和[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="4f3cb-104">`FunctionIDMapper2` 也可讓分析工具指出它是否要接收該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f3cb-105">語法</span><span class="sxs-lookup"><span data-stu-id="4f3cb-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f3cb-106">參數</span><span class="sxs-lookup"><span data-stu-id="4f3cb-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="4f3cb-107">[in] 要重新對應的函式識別項。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="4f3cb-108">[in] 用來區分執行階段的資料指標。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="4f3cb-109">[out] 分析工具所設定的值指標，如果它要接收 `FunctionEnter3`、`FunctionLeave3` 和 `FunctionTailcall3`，或 `FunctionEnter3WithInfo`、`FunctionLeave3WithInfo` 和 `FunctionTailcall3WithInfo` 回呼，則設為 `true`；否則它會將此值設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f3cb-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4f3cb-110">Return Value</span></span>  
 <span data-ttu-id="4f3cb-111">分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="4f3cb-112">傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="4f3cb-113">否則，傳回的 null 值會產生無法預期的結果，包括可能暫止處理序。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f3cb-114">備註</span><span class="sxs-lookup"><span data-stu-id="4f3cb-114">Remarks</span></span>  
 <span data-ttu-id="4f3cb-115">此方法擴充[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式用來傳遞用戶端資料的其他參數。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="4f3cb-116">用戶端資料會用來區分執行階段。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f3cb-117">需求</span><span class="sxs-lookup"><span data-stu-id="4f3cb-117">Requirements</span></span>  
 <span data-ttu-id="4f3cb-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f3cb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f3cb-119">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="4f3cb-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4f3cb-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f3cb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f3cb-121">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f3cb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3cb-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f3cb-122">See also</span></span>

- [<span data-ttu-id="4f3cb-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="4f3cb-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="4f3cb-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="4f3cb-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="4f3cb-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="4f3cb-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="4f3cb-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="4f3cb-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="4f3cb-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="4f3cb-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="4f3cb-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f3cb-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="4f3cb-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f3cb-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="4f3cb-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="4f3cb-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="4f3cb-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="4f3cb-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

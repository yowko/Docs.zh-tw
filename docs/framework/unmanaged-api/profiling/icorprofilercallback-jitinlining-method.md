---
title: ICorProfilerCallback::JITInlining 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866205"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="61ff6-102">ICorProfilerCallback::JITInlining 方法</span><span class="sxs-lookup"><span data-stu-id="61ff6-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="61ff6-103">通知分析工具，及時（JIT）編譯器即將以另一個函式插入函數。</span><span class="sxs-lookup"><span data-stu-id="61ff6-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ff6-104">語法</span><span class="sxs-lookup"><span data-stu-id="61ff6-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61ff6-105">參數</span><span class="sxs-lookup"><span data-stu-id="61ff6-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="61ff6-106">在將插入 `calleeId` 函式的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="61ff6-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="61ff6-107">在要插入之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="61ff6-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="61ff6-108">[out] 允許進行插入的 `true`;否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="61ff6-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61ff6-109">備註</span><span class="sxs-lookup"><span data-stu-id="61ff6-109">Remarks</span></span>  
 <span data-ttu-id="61ff6-110">分析工具可以將 `pfShouldInline` 設定為 `false`，以防止 `calleeId` 函式插入 `callerId` 函數中。</span><span class="sxs-lookup"><span data-stu-id="61ff6-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="61ff6-111">此外，分析工具也可以使用[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_DISABLE_INLINING 值，全域停用內嵌插入。</span><span class="sxs-lookup"><span data-stu-id="61ff6-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="61ff6-112">插入的函式不會引發輸入或離開的事件。</span><span class="sxs-lookup"><span data-stu-id="61ff6-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="61ff6-113">因此，分析工具必須將 `pfShouldInline` 設定為 `false`，才能產生精確的 callgraph。</span><span class="sxs-lookup"><span data-stu-id="61ff6-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="61ff6-114">將 `pfShouldInline` 設定為 `false` 會影響效能，因為內嵌插入通常會增加速度並減少所插入方法的個別 JIT 編譯事件數。</span><span class="sxs-lookup"><span data-stu-id="61ff6-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ff6-115">需求</span><span class="sxs-lookup"><span data-stu-id="61ff6-115">Requirements</span></span>  
 <span data-ttu-id="61ff6-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61ff6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ff6-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61ff6-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61ff6-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61ff6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ff6-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ff6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ff6-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="61ff6-120">See also</span></span>

- [<span data-ttu-id="61ff6-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="61ff6-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

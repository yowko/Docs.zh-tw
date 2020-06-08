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
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500009"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="9a8e5-102">ICorProfilerCallback::JITInlining 方法</span><span class="sxs-lookup"><span data-stu-id="9a8e5-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="9a8e5-103">通知分析工具，及時（JIT）編譯器即將以另一個函式插入函數。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a8e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a8e5-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a8e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="9a8e5-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="9a8e5-106">在將在其中插入函式的函式識別碼 `calleeId` 。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="9a8e5-107">在要插入之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="9a8e5-108">[out] `true`表示允許進行插入;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a8e5-109">備註</span><span class="sxs-lookup"><span data-stu-id="9a8e5-109">Remarks</span></span>  
 <span data-ttu-id="9a8e5-110">分析工具可以將設定 `pfShouldInline` 為 `false` ，以防止函式插入函式 `calleeId` 中 `callerId` 。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="9a8e5-111">此外，分析工具也可以使用[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_DISABLE_INLINING 值，全域停用內嵌插入。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="9a8e5-112">插入的函式不會引發輸入或離開的事件。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="9a8e5-113">因此，分析工具必須將設為，才能 `pfShouldInline` `false` 產生精確的 callgraph。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="9a8e5-114">將設定 `pfShouldInline` 為 `false` 會影響效能，因為內嵌插入通常會增加速度，並減少所插入方法的個別 JIT 編譯事件數目。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a8e5-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="9a8e5-115">Requirements</span></span>  
 <span data-ttu-id="9a8e5-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9a8e5-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a8e5-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a8e5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a8e5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a8e5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a8e5-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a8e5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a8e5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a8e5-120">See also</span></span>

- [<span data-ttu-id="9a8e5-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9a8e5-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

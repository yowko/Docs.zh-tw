---
title: "StackSnapshotCallback 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="15e28-102">StackSnapshotCallback 函式</span><span class="sxs-lookup"><span data-stu-id="15e28-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="15e28-103">提供程式碼剖析工具相關資訊每個 managed 的框架和每次執行未受管理的框架的堆疊上堆疊查核行程，由起始期間[icorprofilerinfo2:: Dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="15e28-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e28-104">語法</span><span class="sxs-lookup"><span data-stu-id="15e28-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15e28-105">參數</span><span class="sxs-lookup"><span data-stu-id="15e28-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="15e28-106">[in]如果此值為零，這個回呼位於執行的未受管理的框架。否則，它是 managed 函式的識別碼，這個回呼位於個 managed 框架。</span><span class="sxs-lookup"><span data-stu-id="15e28-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="15e28-107">[in]原生程式碼指令指標框架中的值。</span><span class="sxs-lookup"><span data-stu-id="15e28-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="15e28-108">[in]A`COR_PRF_FRAME_INFO`值所參考的堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="15e28-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="15e28-109">只有在這個回呼期間，這個值可供使用。</span><span class="sxs-lookup"><span data-stu-id="15e28-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="15e28-110">[in]大小`CONTEXT`結構，也就由參考`context`參數。</span><span class="sxs-lookup"><span data-stu-id="15e28-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="15e28-111">[in]對 win32 指標`CONTEXT`結構，表示這個畫面格 CPU 的狀態。</span><span class="sxs-lookup"><span data-stu-id="15e28-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="15e28-112">`context`參數是傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，才有效`ICorProfilerInfo2::DoStackSnapshot`。</span><span class="sxs-lookup"><span data-stu-id="15e28-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="15e28-113">[in]用戶端資料，這直接透過傳遞指標`ICorProfilerInfo2::DoStackSnapshot`。</span><span class="sxs-lookup"><span data-stu-id="15e28-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15e28-114">備註</span><span class="sxs-lookup"><span data-stu-id="15e28-114">Remarks</span></span>  
 <span data-ttu-id="15e28-115">`StackSnapshotCallback`函式由程式碼剖析工具寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="15e28-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="15e28-116">您必須限制在執行工作的複雜度`StackSnapshotCallback`。</span><span class="sxs-lookup"><span data-stu-id="15e28-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="15e28-117">例如，當使用`ICorProfilerInfo2::DoStackSnapshot`以非同步的方式，目標執行緒可能持有的鎖定。</span><span class="sxs-lookup"><span data-stu-id="15e28-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="15e28-118">如果內的程式碼`StackSnapshotCallback`需要相同的鎖定，可能發生死結。</span><span class="sxs-lookup"><span data-stu-id="15e28-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="15e28-119">`ICorProfilerInfo2::DoStackSnapshot`方法呼叫`StackSnapshotCallback`managed 框架每一次或一次每一回合的 unmanaged 框架的函式。</span><span class="sxs-lookup"><span data-stu-id="15e28-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="15e28-120">如果`StackSnapshotCallback`稱為 「 執行中的未受管理的框架，分析工具可能會使用暫存器內容 (所參考`context`參數) 來執行它自己的未受管理的堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="15e28-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="15e28-121">在此情況下，Win32`CONTEXT`結構代表最近推送的框架內的未受管理的框架執行的 CPU 狀態。</span><span class="sxs-lookup"><span data-stu-id="15e28-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="15e28-122">雖然 Win32`CONTEXT`結構包含之所有暫存器值，則您應該只依賴的堆疊指標暫存器、 框架指標暫存器、 指令指標暫存器和靜態 （即保留） 值整數暫存器。</span><span class="sxs-lookup"><span data-stu-id="15e28-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e28-123">需求</span><span class="sxs-lookup"><span data-stu-id="15e28-123">Requirements</span></span>  
 <span data-ttu-id="15e28-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15e28-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e28-125">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="15e28-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="15e28-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15e28-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15e28-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e28-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e28-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="15e28-128">See Also</span></span>  
 [<span data-ttu-id="15e28-129">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="15e28-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="15e28-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="15e28-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

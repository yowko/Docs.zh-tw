---
title: StackSnapshotCallback 函式
ms.date: 03/30/2017
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
ms.openlocfilehash: 2d6ca18ce48f69d8c94b465efac2b9fe0e10f070
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685301"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="e97a5-102">StackSnapshotCallback 函式</span><span class="sxs-lookup"><span data-stu-id="e97a5-102">StackSnapshotCallback Function</span></span>

<span data-ttu-id="e97a5-103">提供分析工具，其中包含每個 managed 框架的相關資訊，以及堆疊逐步解說（由 [ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 方法所起始）堆疊中每次執行的非受控框架。</span><span class="sxs-lookup"><span data-stu-id="e97a5-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e97a5-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e97a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="e97a5-105">Parameters</span></span>  

 `funcId`  
 <span data-ttu-id="e97a5-106">在如果此值為零，則此回呼適用于執行非受控框架;否則，它是 managed 函式的識別碼，而此回呼適用于受控框架。</span><span class="sxs-lookup"><span data-stu-id="e97a5-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="e97a5-107">在框架中原生程式碼指令指標的值。</span><span class="sxs-lookup"><span data-stu-id="e97a5-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="e97a5-108">在 `COR_PRF_FRAME_INFO` 值，參考堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e97a5-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="e97a5-109">此值僅適用于在此回呼期間使用。</span><span class="sxs-lookup"><span data-stu-id="e97a5-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e97a5-110">在 `CONTEXT` 參數所參考之結構的大小 `context` 。</span><span class="sxs-lookup"><span data-stu-id="e97a5-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="e97a5-111">在Win32 結構的指標 `CONTEXT` ，表示此框架的 CPU 狀態。</span><span class="sxs-lookup"><span data-stu-id="e97a5-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="e97a5-112">`context`只有在傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，參數才有效 `ICorProfilerInfo2::DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="e97a5-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="e97a5-113">在用戶端資料的指標，從直接傳遞至 `ICorProfilerInfo2::DoStackSnapshot` 。</span><span class="sxs-lookup"><span data-stu-id="e97a5-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e97a5-114">備註</span><span class="sxs-lookup"><span data-stu-id="e97a5-114">Remarks</span></span>  

 <span data-ttu-id="e97a5-115">函式是由分析工具寫入器所 `StackSnapshotCallback` 執行。</span><span class="sxs-lookup"><span data-stu-id="e97a5-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="e97a5-116">您必須限制在中完成工作的複雜度 `StackSnapshotCallback` 。</span><span class="sxs-lookup"><span data-stu-id="e97a5-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="e97a5-117">例如， `ICorProfilerInfo2::DoStackSnapshot` 以非同步方式使用時，目標執行緒可能會持有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e97a5-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="e97a5-118">如果內的程式碼 `StackSnapshotCallback` 需要相同的鎖定，可能會災難接踵而至鎖死。</span><span class="sxs-lookup"><span data-stu-id="e97a5-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="e97a5-119">`ICorProfilerInfo2::DoStackSnapshot`方法會 `StackSnapshotCallback` 針對每個 managed 框架呼叫函式一次，或針對每次執行非受控框架呼叫一次函數。</span><span class="sxs-lookup"><span data-stu-id="e97a5-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="e97a5-120">如果 `StackSnapshotCallback` 呼叫以執行非受控框架，分析工具可能會使用參數所參考的登錄內容 (`context`) 來執行它自己的非受控堆疊逐步解說。</span><span class="sxs-lookup"><span data-stu-id="e97a5-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="e97a5-121">在此情況下，Win32 `CONTEXT` 結構代表未受管理的框架執行內最近推入框架的 CPU 狀態。</span><span class="sxs-lookup"><span data-stu-id="e97a5-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="e97a5-122">雖然 Win32 `CONTEXT` 結構包含所有暫存器的值，但您應該只依賴堆疊指標暫存器、框架指標暫存器、指令指標暫存器的值，以及靜態 (，也就是保留) 整數暫存器。</span><span class="sxs-lookup"><span data-stu-id="e97a5-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e97a5-123">需求</span><span class="sxs-lookup"><span data-stu-id="e97a5-123">Requirements</span></span>  

 <span data-ttu-id="e97a5-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e97a5-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e97a5-125">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="e97a5-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e97a5-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e97a5-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e97a5-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e97a5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97a5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e97a5-128">See also</span></span>

- [<span data-ttu-id="e97a5-129">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="e97a5-129">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="e97a5-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e97a5-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)

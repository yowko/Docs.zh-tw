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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 891423661f45a1167d53385e6e0306fb09487278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000411"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="3e255-102">StackSnapshotCallback 函式</span><span class="sxs-lookup"><span data-stu-id="3e255-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="3e255-103">提供分析工具相關資訊每個 managed 的框架和每次執行的非受控框架在堆疊上堆疊查核行程，這起始期間[ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3e255-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e255-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e255-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3e255-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e255-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="3e255-106">[in]如果此值為零，此回呼是未受管理的畫面格; 的執行否則，它是受管理的函式的識別碼，而且此回呼是個 managed 框架。</span><span class="sxs-lookup"><span data-stu-id="3e255-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="3e255-107">[in]原生程式碼指令指標框架中的值。</span><span class="sxs-lookup"><span data-stu-id="3e255-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="3e255-108">[in]A`COR_PRF_FRAME_INFO`值所參考的堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3e255-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="3e255-109">只在回呼期間，這個值是有效的使用。</span><span class="sxs-lookup"><span data-stu-id="3e255-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="3e255-110">[in]大小`CONTEXT`結構，也就由參考`context`參數。</span><span class="sxs-lookup"><span data-stu-id="3e255-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="3e255-111">[in]Win32 指標`CONTEXT`結構，代表此框架的 CPU 的狀態。</span><span class="sxs-lookup"><span data-stu-id="3e255-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="3e255-112">`context`參數是傳入 COR_PRF_SNAPSHOT_CONTEXT 旗標時，才有效`ICorProfilerInfo2::DoStackSnapshot`。</span><span class="sxs-lookup"><span data-stu-id="3e255-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="3e255-113">[in]用戶端資料指標，再傳遞直接從`ICorProfilerInfo2::DoStackSnapshot`。</span><span class="sxs-lookup"><span data-stu-id="3e255-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e255-114">備註</span><span class="sxs-lookup"><span data-stu-id="3e255-114">Remarks</span></span>  
 <span data-ttu-id="3e255-115">`StackSnapshotCallback`函式由程式碼剖析工具寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="3e255-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="3e255-116">您必須限制在完成工作的複雜性`StackSnapshotCallback`。</span><span class="sxs-lookup"><span data-stu-id="3e255-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="3e255-117">例如，當使用`ICorProfilerInfo2::DoStackSnapshot`以非同步方式，在目標執行緒可能持有的鎖定。</span><span class="sxs-lookup"><span data-stu-id="3e255-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="3e255-118">如果程式碼內`StackSnapshotCallback`需要相同的鎖定，可能發生死結。</span><span class="sxs-lookup"><span data-stu-id="3e255-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="3e255-119">`ICorProfilerInfo2::DoStackSnapshot`方法呼叫`StackSnapshotCallback`managed 框架每一次或一次每一回合的非受控框架的函式。</span><span class="sxs-lookup"><span data-stu-id="3e255-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="3e255-120">如果`StackSnapshotCallback`呼叫執行未受管理的畫面格期間，分析工具可以使用暫存器內容 (藉由參考`context`參數) 來執行它自己的未受管理的堆疊查核行程。</span><span class="sxs-lookup"><span data-stu-id="3e255-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="3e255-121">在此案例中，Win32`CONTEXT`結構代表最近推送的框架內的未受管理的框架執行的 CPU 狀態。</span><span class="sxs-lookup"><span data-stu-id="3e255-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="3e255-122">雖然 Win32`CONTEXT`結構包含的所有暫存器值，您應該只依賴堆疊指標暫存器、 框架指標暫存器、 指令指標暫存器和值 （也就，保留） 之靜態整數暫存器。</span><span class="sxs-lookup"><span data-stu-id="3e255-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e255-123">需求</span><span class="sxs-lookup"><span data-stu-id="3e255-123">Requirements</span></span>  
 <span data-ttu-id="3e255-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e255-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e255-125">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3e255-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3e255-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e255-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e255-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e255-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e255-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e255-128">See also</span></span>

- [<span data-ttu-id="3e255-129">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="3e255-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="3e255-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3e255-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)

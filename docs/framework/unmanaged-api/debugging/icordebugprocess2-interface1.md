---
title: ICorDebugProcess2 Interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b3bb51f307093ea1cc8cc45064d5c405974822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948836"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="feca8-102">ICorDebugProcess2 Interface</span><span class="sxs-lookup"><span data-stu-id="feca8-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="feca8-103">ICorDebugProcess 介面，表示處理程序執行 managed 程式碼的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="feca8-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="feca8-104">方法</span><span class="sxs-lookup"><span data-stu-id="feca8-104">Methods</span></span>  
  
|<span data-ttu-id="feca8-105">方法</span><span class="sxs-lookup"><span data-stu-id="feca8-105">Method</span></span>|<span data-ttu-id="feca8-106">描述</span><span class="sxs-lookup"><span data-stu-id="feca8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="feca8-107">ClearUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="feca8-108">移除指定之位移的先前呼叫所設定的中斷點`ICorDebugProcess2::SetUnmanagedBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="feca8-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="feca8-109">GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="feca8-110">取得必須設為 common language runtime (CLR) 將影像載入處理序所參考的旗標`ICorDebugProcess2`。</span><span class="sxs-lookup"><span data-stu-id="feca8-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="feca8-111">GetReferenceValueFromGCHandle 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="feca8-112">取得指定已處理的記憶體回收的 managed 物件的參考指標。</span><span class="sxs-lookup"><span data-stu-id="feca8-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="feca8-113">GetThreadForTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="feca8-114">取得具有指定識別碼的工作正在執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="feca8-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="feca8-115">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="feca8-116">取得正在偵錯處理序正在執行的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="feca8-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="feca8-117">SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="feca8-118">設定所需的影像載入處理序偵錯在 just-in-time (JIT) 編譯器的旗標。</span><span class="sxs-lookup"><span data-stu-id="feca8-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="feca8-119">SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="feca8-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="feca8-120">指定的原生映像的位移設定為未受管理的中斷點。</span><span class="sxs-lookup"><span data-stu-id="feca8-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feca8-121">備註</span><span class="sxs-lookup"><span data-stu-id="feca8-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feca8-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="feca8-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feca8-123">需求</span><span class="sxs-lookup"><span data-stu-id="feca8-123">Requirements</span></span>  
 <span data-ttu-id="feca8-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="feca8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feca8-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="feca8-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="feca8-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="feca8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feca8-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feca8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feca8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feca8-128">See also</span></span>

- [<span data-ttu-id="feca8-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="feca8-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

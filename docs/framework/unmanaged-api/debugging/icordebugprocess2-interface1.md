---
title: ICorDebugProcess2 介面
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
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965679"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="7b5e4-102">ICorDebugProcess2 介面</span><span class="sxs-lookup"><span data-stu-id="7b5e4-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="7b5e4-103">ICorDebugProcess 介面，表示處理程序執行 managed 程式碼的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b5e4-104">方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-104">Methods</span></span>  
  
|<span data-ttu-id="7b5e4-105">方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-105">Method</span></span>|<span data-ttu-id="7b5e4-106">描述</span><span class="sxs-lookup"><span data-stu-id="7b5e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b5e4-107">ClearUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="7b5e4-108">移除指定之位移的先前呼叫所設定的中斷點`ICorDebugProcess2::SetUnmanagedBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="7b5e4-109">GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="7b5e4-110">取得必須設為 common language runtime (CLR) 將影像載入處理序所參考的旗標`ICorDebugProcess2`。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="7b5e4-111">GetReferenceValueFromGCHandle 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="7b5e4-112">取得指定已處理的記憶體回收的 managed 物件的參考指標。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="7b5e4-113">GetThreadForTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="7b5e4-114">取得具有指定識別碼的工作正在執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="7b5e4-115">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="7b5e4-116">取得正在偵錯處理序正在執行的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="7b5e4-117">SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="7b5e4-118">設定所需的影像載入處理序偵錯在 just-in-time (JIT) 編譯器的旗標。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="7b5e4-119">SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="7b5e4-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="7b5e4-120">指定的原生映像的位移設定為未受管理的中斷點。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b5e4-121">備註</span><span class="sxs-lookup"><span data-stu-id="7b5e4-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b5e4-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b5e4-123">需求</span><span class="sxs-lookup"><span data-stu-id="7b5e4-123">Requirements</span></span>  
 <span data-ttu-id="7b5e4-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b5e4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b5e4-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b5e4-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b5e4-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b5e4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b5e4-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b5e4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b5e4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b5e4-128">See also</span></span>
- [<span data-ttu-id="7b5e4-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7b5e4-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

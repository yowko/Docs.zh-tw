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
ms.openlocfilehash: 5519714ff2b4ee67d0e59001bf5b454cdc25d648
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961072"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="a641e-102">ICorDebugProcess2 Interface</span><span class="sxs-lookup"><span data-stu-id="a641e-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="a641e-103">ICorDebugProcess 介面的邏輯延伸, 代表執行 managed 程式碼的進程。</span><span class="sxs-lookup"><span data-stu-id="a641e-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a641e-104">方法</span><span class="sxs-lookup"><span data-stu-id="a641e-104">Methods</span></span>  
  
|<span data-ttu-id="a641e-105">方法</span><span class="sxs-lookup"><span data-stu-id="a641e-105">Method</span></span>|<span data-ttu-id="a641e-106">描述</span><span class="sxs-lookup"><span data-stu-id="a641e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a641e-107">ClearUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="a641e-108">移除先前呼叫`ICorDebugProcess2::SetUnmanagedBreakpoint`所設定之指定位移處的中斷點。</span><span class="sxs-lookup"><span data-stu-id="a641e-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="a641e-109">GetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="a641e-110">取得必須針對 common language runtime (CLR) 設定的旗標, 以便將影像載入這個`ICorDebugProcess2`所參考的進程中。</span><span class="sxs-lookup"><span data-stu-id="a641e-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="a641e-111">GetReferenceValueFromGCHandle 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="a641e-112">取得具有垃圾收集控制碼之指定 managed 物件的參考指標。</span><span class="sxs-lookup"><span data-stu-id="a641e-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="a641e-113">GetThreadForTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="a641e-114">取得具有指定識別碼之工作執行所在的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a641e-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="a641e-115">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="a641e-116">取得正在進行偵錯工具的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="a641e-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="a641e-117">SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="a641e-118">設定即時 (JIT) 編譯器所需的旗標, 以將影像載入正在進行調試的進程。</span><span class="sxs-lookup"><span data-stu-id="a641e-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="a641e-119">SetUnmanagedBreakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="a641e-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="a641e-120">在指定的原生映射位移處設定非受控中斷點。</span><span class="sxs-lookup"><span data-stu-id="a641e-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a641e-121">備註</span><span class="sxs-lookup"><span data-stu-id="a641e-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a641e-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a641e-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a641e-123">需求</span><span class="sxs-lookup"><span data-stu-id="a641e-123">Requirements</span></span>  
 <span data-ttu-id="a641e-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a641e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a641e-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a641e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a641e-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a641e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a641e-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a641e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a641e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a641e-128">See also</span></span>

- [<span data-ttu-id="a641e-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a641e-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

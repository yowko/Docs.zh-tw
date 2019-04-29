---
title: ICorDebugFunctionBreakpoint 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f15b9f5961699f905e765426576bdf6f3416793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651645"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="3416f-102">ICorDebugFunctionBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="3416f-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="3416f-103">擴充 ICorDebugBreakpoint 介面，以支援在函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="3416f-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3416f-104">方法</span><span class="sxs-lookup"><span data-stu-id="3416f-104">Methods</span></span>  
  
|<span data-ttu-id="3416f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3416f-105">Method</span></span>|<span data-ttu-id="3416f-106">描述</span><span class="sxs-lookup"><span data-stu-id="3416f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3416f-107">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="3416f-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="3416f-108">取得參考函式設定中斷點 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="3416f-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="3416f-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="3416f-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="3416f-110">取得中斷點的函式中的位移。</span><span class="sxs-lookup"><span data-stu-id="3416f-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3416f-111">備註</span><span class="sxs-lookup"><span data-stu-id="3416f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3416f-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="3416f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3416f-113">需求</span><span class="sxs-lookup"><span data-stu-id="3416f-113">Requirements</span></span>  
 <span data-ttu-id="3416f-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3416f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3416f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3416f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3416f-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3416f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3416f-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3416f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3416f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3416f-118">See also</span></span>

- [<span data-ttu-id="3416f-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3416f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugBreakpoint 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a68e061c6def61746ee65f8a25818f8dbcd785b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645353"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="50ce7-102">ICorDebugBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="50ce7-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="50ce7-103">表示函式或在值上的監看點的中斷點。</span><span class="sxs-lookup"><span data-stu-id="50ce7-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50ce7-104">方法</span><span class="sxs-lookup"><span data-stu-id="50ce7-104">Methods</span></span>  
  
|<span data-ttu-id="50ce7-105">方法</span><span class="sxs-lookup"><span data-stu-id="50ce7-105">Method</span></span>|<span data-ttu-id="50ce7-106">描述</span><span class="sxs-lookup"><span data-stu-id="50ce7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50ce7-107">Activate 方法</span><span class="sxs-lookup"><span data-stu-id="50ce7-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="50ce7-108">設定作用中的狀態，這個`ICorDebugBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="50ce7-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="50ce7-109">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="50ce7-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="50ce7-110">取得值，指出是否此`ICorDebugBreakpoint`作用中。</span><span class="sxs-lookup"><span data-stu-id="50ce7-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50ce7-111">備註</span><span class="sxs-lookup"><span data-stu-id="50ce7-111">Remarks</span></span>  
 <span data-ttu-id="50ce7-112">中斷點不直接支援條件式運算式。</span><span class="sxs-lookup"><span data-stu-id="50ce7-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="50ce7-113">如果需要這類功能，則偵錯工具必須實作它的上方`ICorDebugBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="50ce7-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="50ce7-114">ICorDebugFunctionBreakpoint 介面會擴充`ICorDebugBreakpoint`支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="50ce7-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50ce7-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="50ce7-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50ce7-116">需求</span><span class="sxs-lookup"><span data-stu-id="50ce7-116">Requirements</span></span>  
 <span data-ttu-id="50ce7-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50ce7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50ce7-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50ce7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50ce7-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50ce7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50ce7-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50ce7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ce7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50ce7-121">See also</span></span>

- [<span data-ttu-id="50ce7-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="50ce7-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

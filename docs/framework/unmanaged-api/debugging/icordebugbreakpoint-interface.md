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
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784380"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="e3a36-102">ICorDebugBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="e3a36-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="e3a36-103">代表函式中的中斷點，或值的監看點。</span><span class="sxs-lookup"><span data-stu-id="e3a36-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3a36-104">方法</span><span class="sxs-lookup"><span data-stu-id="e3a36-104">Methods</span></span>  
  
|<span data-ttu-id="e3a36-105">方法</span><span class="sxs-lookup"><span data-stu-id="e3a36-105">Method</span></span>|<span data-ttu-id="e3a36-106">描述</span><span class="sxs-lookup"><span data-stu-id="e3a36-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3a36-107">Activate 方法</span><span class="sxs-lookup"><span data-stu-id="e3a36-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="e3a36-108">設定此 `ICorDebugBreakpoint`的作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="e3a36-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="e3a36-109">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="e3a36-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="e3a36-110">取得值，指出此 `ICorDebugBreakpoint` 是否為使用中。</span><span class="sxs-lookup"><span data-stu-id="e3a36-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3a36-111">備註</span><span class="sxs-lookup"><span data-stu-id="e3a36-111">Remarks</span></span>  
 <span data-ttu-id="e3a36-112">中斷點不直接支援條件運算式。</span><span class="sxs-lookup"><span data-stu-id="e3a36-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="e3a36-113">如果需要這類功能，偵錯工具必須在 `ICorDebugBreakpoint`上執行。</span><span class="sxs-lookup"><span data-stu-id="e3a36-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="e3a36-114">ICorDebugFunctionBreakpoint 介面會擴充 `ICorDebugBreakpoint`，以支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="e3a36-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3a36-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e3a36-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3a36-116">需求</span><span class="sxs-lookup"><span data-stu-id="e3a36-116">Requirements</span></span>  
 <span data-ttu-id="e3a36-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3a36-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3a36-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3a36-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3a36-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3a36-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3a36-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3a36-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a36-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="e3a36-121">See also</span></span>

- [<span data-ttu-id="e3a36-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e3a36-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

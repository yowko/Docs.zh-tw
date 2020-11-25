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
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730197"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="98a35-102">ICorDebugBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="98a35-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="98a35-103">表示函式中的中斷點，或值的監看點。</span><span class="sxs-lookup"><span data-stu-id="98a35-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98a35-104">方法</span><span class="sxs-lookup"><span data-stu-id="98a35-104">Methods</span></span>  
  
|<span data-ttu-id="98a35-105">方法</span><span class="sxs-lookup"><span data-stu-id="98a35-105">Method</span></span>|<span data-ttu-id="98a35-106">描述</span><span class="sxs-lookup"><span data-stu-id="98a35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98a35-107">Activate 方法</span><span class="sxs-lookup"><span data-stu-id="98a35-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="98a35-108">設定這個的作用中狀態 `ICorDebugBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="98a35-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="98a35-109">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="98a35-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="98a35-110">取得值，這個值表示這是否 `ICorDebugBreakpoint` 為使用中。</span><span class="sxs-lookup"><span data-stu-id="98a35-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98a35-111">備註</span><span class="sxs-lookup"><span data-stu-id="98a35-111">Remarks</span></span>  

 <span data-ttu-id="98a35-112">中斷點不會直接支援條件運算式。</span><span class="sxs-lookup"><span data-stu-id="98a35-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="98a35-113">如果需要這類功能，偵錯工具必須在上執行 `ICorDebugBreakpoint` 。</span><span class="sxs-lookup"><span data-stu-id="98a35-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="98a35-114">ICorDebugFunctionBreakpoint 介面會擴充 `ICorDebugBreakpoint` 以支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="98a35-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98a35-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="98a35-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a35-116">需求</span><span class="sxs-lookup"><span data-stu-id="98a35-116">Requirements</span></span>  

 <span data-ttu-id="98a35-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="98a35-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a35-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a35-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a35-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a35-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a35-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a35-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a35-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a35-121">See also</span></span>

- [<span data-ttu-id="98a35-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="98a35-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugBreakpoint Interface1
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd2c4245b5e3dcc4f7b989a3ca9add8d568467cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="b7212-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="b7212-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="b7212-103">表示函式或監看式上的點值中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="b7212-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7212-104">方法</span><span class="sxs-lookup"><span data-stu-id="b7212-104">Methods</span></span>  
  
|<span data-ttu-id="b7212-105">方法</span><span class="sxs-lookup"><span data-stu-id="b7212-105">Method</span></span>|<span data-ttu-id="b7212-106">描述</span><span class="sxs-lookup"><span data-stu-id="b7212-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7212-107">Activate 方法</span><span class="sxs-lookup"><span data-stu-id="b7212-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="b7212-108">設定這個的使用中狀態`ICorDebugBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="b7212-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="b7212-109">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="b7212-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="b7212-110">取得值，指出是否此`ICorDebugBreakpoint`為作用中。</span><span class="sxs-lookup"><span data-stu-id="b7212-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7212-111">備註</span><span class="sxs-lookup"><span data-stu-id="b7212-111">Remarks</span></span>  
 <span data-ttu-id="b7212-112">中斷點不直接支援條件式運算式。</span><span class="sxs-lookup"><span data-stu-id="b7212-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="b7212-113">如果想要使用這類功能，偵錯工具必須實作它最上層的`ICorDebugBreakpoint`。</span><span class="sxs-lookup"><span data-stu-id="b7212-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="b7212-114">ICorDebugFunctionBreakpoint 介面延伸`ICorDebugBreakpoint`支援函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="b7212-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7212-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b7212-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7212-116">需求</span><span class="sxs-lookup"><span data-stu-id="b7212-116">Requirements</span></span>  
 <span data-ttu-id="b7212-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7212-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7212-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7212-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7212-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7212-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7212-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7212-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7212-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7212-121">See Also</span></span>  
 [<span data-ttu-id="b7212-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b7212-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

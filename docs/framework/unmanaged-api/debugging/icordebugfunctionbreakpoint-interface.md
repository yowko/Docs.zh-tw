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
ms.openlocfilehash: 2c3c11d3b6a6daec7b35377ef24557dd5077af21
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977717"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="c0ed1-102">ICorDebugFunctionBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="c0ed1-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="c0ed1-103">擴充 ICorDebugBreakpoint 介面，以支援在函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="c0ed1-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0ed1-104">方法</span><span class="sxs-lookup"><span data-stu-id="c0ed1-104">Methods</span></span>  
  
|<span data-ttu-id="c0ed1-105">方法</span><span class="sxs-lookup"><span data-stu-id="c0ed1-105">Method</span></span>|<span data-ttu-id="c0ed1-106">描述</span><span class="sxs-lookup"><span data-stu-id="c0ed1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0ed1-107">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="c0ed1-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="c0ed1-108">取得參考函式設定中斷點 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="c0ed1-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="c0ed1-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c0ed1-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="c0ed1-110">取得中斷點的函式中的位移。</span><span class="sxs-lookup"><span data-stu-id="c0ed1-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0ed1-111">備註</span><span class="sxs-lookup"><span data-stu-id="c0ed1-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0ed1-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c0ed1-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0ed1-113">需求</span><span class="sxs-lookup"><span data-stu-id="c0ed1-113">Requirements</span></span>  
 <span data-ttu-id="c0ed1-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0ed1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0ed1-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0ed1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0ed1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0ed1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0ed1-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0ed1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ed1-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0ed1-118">See also</span></span>
- [<span data-ttu-id="c0ed1-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c0ed1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugFunctionBreakpoint Interface1
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
ms.openlocfilehash: 6cd4c430798333dd22c36ce30e7c9ce05bdc8f56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414179"
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="850d8-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="850d8-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="850d8-103">擴充 ICorDebugBreakpoint 介面以支援在函式內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="850d8-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="850d8-104">方法</span><span class="sxs-lookup"><span data-stu-id="850d8-104">Methods</span></span>  
  
|<span data-ttu-id="850d8-105">方法</span><span class="sxs-lookup"><span data-stu-id="850d8-105">Method</span></span>|<span data-ttu-id="850d8-106">描述</span><span class="sxs-lookup"><span data-stu-id="850d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="850d8-107">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="850d8-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="850d8-108">取得參考函式設定中斷點 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="850d8-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="850d8-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="850d8-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="850d8-110">取得，中斷點在函式內的位移。</span><span class="sxs-lookup"><span data-stu-id="850d8-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="850d8-111">備註</span><span class="sxs-lookup"><span data-stu-id="850d8-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="850d8-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="850d8-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="850d8-113">需求</span><span class="sxs-lookup"><span data-stu-id="850d8-113">Requirements</span></span>  
 <span data-ttu-id="850d8-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="850d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="850d8-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="850d8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="850d8-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="850d8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="850d8-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="850d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="850d8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="850d8-118">See Also</span></span>  
 [<span data-ttu-id="850d8-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="850d8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

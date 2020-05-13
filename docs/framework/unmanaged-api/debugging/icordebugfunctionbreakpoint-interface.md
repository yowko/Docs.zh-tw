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
ms.openlocfilehash: 6a378e3579ab9ea8d9534a408d0e456373616cad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213132"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="36209-102">ICorDebugFunctionBreakpoint 介面</span><span class="sxs-lookup"><span data-stu-id="36209-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="36209-103">擴充 ICorDebugBreakpoint 介面，以支援函數內的中斷點。</span><span class="sxs-lookup"><span data-stu-id="36209-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36209-104">方法</span><span class="sxs-lookup"><span data-stu-id="36209-104">Methods</span></span>  
  
|<span data-ttu-id="36209-105">方法</span><span class="sxs-lookup"><span data-stu-id="36209-105">Method</span></span>|<span data-ttu-id="36209-106">描述</span><span class="sxs-lookup"><span data-stu-id="36209-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36209-107">GetFunction 方法</span><span class="sxs-lookup"><span data-stu-id="36209-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="36209-108">取得參考已設定中斷點之函數的 ICorDebugFunction 介面指標。</span><span class="sxs-lookup"><span data-stu-id="36209-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="36209-109">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="36209-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="36209-110">取得函式內中斷點的位移。</span><span class="sxs-lookup"><span data-stu-id="36209-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36209-111">備註</span><span class="sxs-lookup"><span data-stu-id="36209-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36209-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="36209-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36209-113">需求</span><span class="sxs-lookup"><span data-stu-id="36209-113">Requirements</span></span>  
 <span data-ttu-id="36209-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36209-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36209-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36209-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36209-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36209-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36209-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36209-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36209-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="36209-118">See also</span></span>

- [<span data-ttu-id="36209-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="36209-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

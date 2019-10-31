---
title: ICorDebugBreakpointEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 5fb4a8a508cde4455bbee8c08432d3549e3fac43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122761"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="d47dc-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d47dc-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="d47dc-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="d47dc-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d47dc-104">方法</span><span class="sxs-lookup"><span data-stu-id="d47dc-104">Methods</span></span>  
  
|<span data-ttu-id="d47dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="d47dc-105">Method</span></span>|<span data-ttu-id="d47dc-106">描述</span><span class="sxs-lookup"><span data-stu-id="d47dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d47dc-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="d47dc-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="d47dc-108">從列舉中取得指定數目的 `ICorDebugBreakpoint` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="d47dc-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d47dc-109">備註</span><span class="sxs-lookup"><span data-stu-id="d47dc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d47dc-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d47dc-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d47dc-111">需求</span><span class="sxs-lookup"><span data-stu-id="d47dc-111">Requirements</span></span>  
 <span data-ttu-id="d47dc-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d47dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d47dc-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d47dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d47dc-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d47dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d47dc-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d47dc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d47dc-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d47dc-116">See also</span></span>

- [<span data-ttu-id="d47dc-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d47dc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

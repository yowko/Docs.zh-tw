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
ms.openlocfilehash: 22ae1d24040a8ee5000e0ff2fbeb2b45e08050df
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784347"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="daccd-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="daccd-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="daccd-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="daccd-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="daccd-104">方法</span><span class="sxs-lookup"><span data-stu-id="daccd-104">Methods</span></span>  
  
|<span data-ttu-id="daccd-105">方法</span><span class="sxs-lookup"><span data-stu-id="daccd-105">Method</span></span>|<span data-ttu-id="daccd-106">描述</span><span class="sxs-lookup"><span data-stu-id="daccd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="daccd-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="daccd-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="daccd-108">從列舉中取得指定數目的 `ICorDebugBreakpoint` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="daccd-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daccd-109">備註</span><span class="sxs-lookup"><span data-stu-id="daccd-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daccd-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="daccd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daccd-111">需求</span><span class="sxs-lookup"><span data-stu-id="daccd-111">Requirements</span></span>  
 <span data-ttu-id="daccd-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="daccd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daccd-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="daccd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daccd-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daccd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daccd-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daccd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daccd-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="daccd-116">See also</span></span>

- [<span data-ttu-id="daccd-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="daccd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

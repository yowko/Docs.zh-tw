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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8192bd7ccaebab78158f11adb79509031132ecd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937009"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="d7562-102">ICorDebugBreakpointEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d7562-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="d7562-103">會執行 ICorDebugEnum 方法, 並列舉 ICorDebugBreakpoint 陣列。</span><span class="sxs-lookup"><span data-stu-id="d7562-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7562-104">方法</span><span class="sxs-lookup"><span data-stu-id="d7562-104">Methods</span></span>  
  
|<span data-ttu-id="d7562-105">方法</span><span class="sxs-lookup"><span data-stu-id="d7562-105">Method</span></span>|<span data-ttu-id="d7562-106">描述</span><span class="sxs-lookup"><span data-stu-id="d7562-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7562-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="d7562-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="d7562-108">從列舉中取得指定`ICorDebugBreakpoint`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="d7562-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7562-109">備註</span><span class="sxs-lookup"><span data-stu-id="d7562-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7562-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d7562-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7562-111">需求</span><span class="sxs-lookup"><span data-stu-id="d7562-111">Requirements</span></span>  
 <span data-ttu-id="d7562-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7562-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7562-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7562-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7562-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7562-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7562-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7562-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7562-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7562-116">See also</span></span>

- [<span data-ttu-id="d7562-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d7562-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

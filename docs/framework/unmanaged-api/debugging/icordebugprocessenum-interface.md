---
title: ICorDebugProcessEnum Interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81653c69353b60d7287240505f53b26552c21774
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960983"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="7d4f9-102">ICorDebugProcessEnum Interface</span><span class="sxs-lookup"><span data-stu-id="7d4f9-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="7d4f9-103">會執行 ICorDebugEnum 方法並列舉 ICorDebugProcess 陣列。</span><span class="sxs-lookup"><span data-stu-id="7d4f9-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d4f9-104">方法</span><span class="sxs-lookup"><span data-stu-id="7d4f9-104">Methods</span></span>  
  
|<span data-ttu-id="7d4f9-105">方法</span><span class="sxs-lookup"><span data-stu-id="7d4f9-105">Method</span></span>|<span data-ttu-id="7d4f9-106">描述</span><span class="sxs-lookup"><span data-stu-id="7d4f9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d4f9-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="7d4f9-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="7d4f9-108">從列舉中取得指定`ICorDebugProcess`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="7d4f9-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d4f9-109">備註</span><span class="sxs-lookup"><span data-stu-id="7d4f9-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d4f9-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7d4f9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d4f9-111">需求</span><span class="sxs-lookup"><span data-stu-id="7d4f9-111">Requirements</span></span>  
 <span data-ttu-id="7d4f9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d4f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d4f9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d4f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d4f9-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d4f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d4f9-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d4f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4f9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d4f9-116">See also</span></span>

- [<span data-ttu-id="7d4f9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7d4f9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

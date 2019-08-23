---
title: ICorDebugStepperEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum
helpviewer_keywords:
- ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7336f958019c2f696a9b1a26b075c076cfc84f5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953024"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="351a1-102">ICorDebugStepperEnum 介面</span><span class="sxs-lookup"><span data-stu-id="351a1-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="351a1-103">會執行 ICorDebugEnum 方法, 並列舉 ICorDebugStepper 陣列。</span><span class="sxs-lookup"><span data-stu-id="351a1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="351a1-104">方法</span><span class="sxs-lookup"><span data-stu-id="351a1-104">Methods</span></span>  
  
|<span data-ttu-id="351a1-105">方法</span><span class="sxs-lookup"><span data-stu-id="351a1-105">Method</span></span>|<span data-ttu-id="351a1-106">描述</span><span class="sxs-lookup"><span data-stu-id="351a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="351a1-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="351a1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="351a1-108">從列舉中取得指定`ICorDebugStepper`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="351a1-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="351a1-109">備註</span><span class="sxs-lookup"><span data-stu-id="351a1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="351a1-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="351a1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="351a1-111">需求</span><span class="sxs-lookup"><span data-stu-id="351a1-111">Requirements</span></span>  
 <span data-ttu-id="351a1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="351a1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="351a1-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="351a1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="351a1-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="351a1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="351a1-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="351a1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="351a1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="351a1-116">See also</span></span>

- [<span data-ttu-id="351a1-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="351a1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

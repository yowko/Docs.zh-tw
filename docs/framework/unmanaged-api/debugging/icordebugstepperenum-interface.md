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
ms.openlocfilehash: 89552a099241f1bec61f9aa8a8321ef9932e886c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173221"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="3ee4f-102">ICorDebugStepperEnum 介面</span><span class="sxs-lookup"><span data-stu-id="3ee4f-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="3ee4f-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugStepper 陣列。</span><span class="sxs-lookup"><span data-stu-id="3ee4f-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ee4f-104">方法</span><span class="sxs-lookup"><span data-stu-id="3ee4f-104">Methods</span></span>  
  
|<span data-ttu-id="3ee4f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3ee4f-105">Method</span></span>|<span data-ttu-id="3ee4f-106">描述</span><span class="sxs-lookup"><span data-stu-id="3ee4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ee4f-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="3ee4f-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="3ee4f-108">取得指定的數目`ICorDebugStepper`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ee4f-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ee4f-109">備註</span><span class="sxs-lookup"><span data-stu-id="3ee4f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ee4f-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="3ee4f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ee4f-111">需求</span><span class="sxs-lookup"><span data-stu-id="3ee4f-111">Requirements</span></span>  
 <span data-ttu-id="3ee4f-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ee4f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ee4f-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ee4f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ee4f-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ee4f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ee4f-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ee4f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee4f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ee4f-116">See also</span></span>

- [<span data-ttu-id="3ee4f-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3ee4f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

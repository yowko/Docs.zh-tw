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
ms.openlocfilehash: facea5cd7f0b0e0e6c0b1049e87a2355f1d3965a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697164"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="0a559-102">ICorDebugStepperEnum 介面</span><span class="sxs-lookup"><span data-stu-id="0a559-102">ICorDebugStepperEnum Interface</span></span>

<span data-ttu-id="0a559-103">會實 ICorDebugEnum 方法，並列舉 ICorDebugStepper 陣列。</span><span class="sxs-lookup"><span data-stu-id="0a559-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a559-104">方法</span><span class="sxs-lookup"><span data-stu-id="0a559-104">Methods</span></span>  
  
|<span data-ttu-id="0a559-105">方法</span><span class="sxs-lookup"><span data-stu-id="0a559-105">Method</span></span>|<span data-ttu-id="0a559-106">描述</span><span class="sxs-lookup"><span data-stu-id="0a559-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a559-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="0a559-107">Next Method</span></span>](icordebugstepperenum-next-method.md)|<span data-ttu-id="0a559-108">`ICorDebugStepper`從目前位置開始，取得列舉的指定實例數目。</span><span class="sxs-lookup"><span data-stu-id="0a559-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a559-109">備註</span><span class="sxs-lookup"><span data-stu-id="0a559-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a559-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0a559-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a559-111">需求</span><span class="sxs-lookup"><span data-stu-id="0a559-111">Requirements</span></span>  

 <span data-ttu-id="0a559-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a559-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a559-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a559-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a559-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a559-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a559-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a559-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a559-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a559-116">See also</span></span>

- [<span data-ttu-id="0a559-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0a559-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

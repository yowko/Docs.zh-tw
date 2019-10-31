---
title: ICorDebugCodeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: f4baaf5e4f5117ee936fa6d758798c340551c48b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121073"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="e0776-102">ICorDebugCodeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e0776-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="e0776-103">會執行 "ICorDebugEnum" 方法，並列舉 "ICorDebugCode" 陣列。</span><span class="sxs-lookup"><span data-stu-id="e0776-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e0776-104">方法</span><span class="sxs-lookup"><span data-stu-id="e0776-104">Methods</span></span>  
  
|<span data-ttu-id="e0776-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0776-105">Method</span></span>|<span data-ttu-id="e0776-106">描述</span><span class="sxs-lookup"><span data-stu-id="e0776-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e0776-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="e0776-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-next-method.md)|<span data-ttu-id="e0776-108">從列舉中取得指定數目的 `ICorDebugCode` 實例，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="e0776-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0776-109">備註</span><span class="sxs-lookup"><span data-stu-id="e0776-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0776-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e0776-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0776-111">需求</span><span class="sxs-lookup"><span data-stu-id="e0776-111">Requirements</span></span>  
 <span data-ttu-id="e0776-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0776-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0776-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0776-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0776-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0776-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0776-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0776-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0776-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0776-116">See also</span></span>

- [<span data-ttu-id="e0776-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0776-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

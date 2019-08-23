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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a771100ad4d63173fdb3b1ddea5ae3d67fbbc7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960680"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="70378-102">ICorDebugCodeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="70378-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="70378-103">會執行 "ICorDebugEnum" 方法, 並列舉 "ICorDebugCode" 陣列。</span><span class="sxs-lookup"><span data-stu-id="70378-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70378-104">方法</span><span class="sxs-lookup"><span data-stu-id="70378-104">Methods</span></span>  
  
|<span data-ttu-id="70378-105">方法</span><span class="sxs-lookup"><span data-stu-id="70378-105">Method</span></span>|<span data-ttu-id="70378-106">描述</span><span class="sxs-lookup"><span data-stu-id="70378-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70378-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="70378-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-next-method.md)|<span data-ttu-id="70378-108">從列舉中取得指定`ICorDebugCode`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="70378-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70378-109">備註</span><span class="sxs-lookup"><span data-stu-id="70378-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70378-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="70378-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70378-111">需求</span><span class="sxs-lookup"><span data-stu-id="70378-111">Requirements</span></span>  
 <span data-ttu-id="70378-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70378-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70378-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70378-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70378-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70378-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70378-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70378-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70378-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70378-116">See also</span></span>

- [<span data-ttu-id="70378-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70378-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

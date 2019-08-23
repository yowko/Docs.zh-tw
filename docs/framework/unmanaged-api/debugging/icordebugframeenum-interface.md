---
title: ICorDebugFrameEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9ea398c32762be31f93002533b15bcf3851b870
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910236"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="11e0a-102">ICorDebugFrameEnum 介面</span><span class="sxs-lookup"><span data-stu-id="11e0a-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="11e0a-103">會執行 ICorDebugEnum 方法, 並列舉 ICorDebugFrame 陣列。</span><span class="sxs-lookup"><span data-stu-id="11e0a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11e0a-104">方法</span><span class="sxs-lookup"><span data-stu-id="11e0a-104">Methods</span></span>  
  
|<span data-ttu-id="11e0a-105">方法</span><span class="sxs-lookup"><span data-stu-id="11e0a-105">Method</span></span>|<span data-ttu-id="11e0a-106">說明</span><span class="sxs-lookup"><span data-stu-id="11e0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11e0a-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="11e0a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="11e0a-108">從列舉中取得指定`ICorDebugFrame`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="11e0a-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11e0a-109">備註</span><span class="sxs-lookup"><span data-stu-id="11e0a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11e0a-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="11e0a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e0a-111">需求</span><span class="sxs-lookup"><span data-stu-id="11e0a-111">Requirements</span></span>  
 <span data-ttu-id="11e0a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11e0a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e0a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11e0a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11e0a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11e0a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11e0a-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e0a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e0a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11e0a-116">See also</span></span>

- [<span data-ttu-id="11e0a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="11e0a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

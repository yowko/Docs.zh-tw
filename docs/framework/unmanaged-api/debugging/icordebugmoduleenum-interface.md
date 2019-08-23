---
title: ICorDebugModuleEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 682fe190126d4f40013678d996804e9f3481bc02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965076"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="a8474-102">ICorDebugModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a8474-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="a8474-103">會執行 ICorDebugEnum 方法, 並列舉 ICorDebugModule 陣列。</span><span class="sxs-lookup"><span data-stu-id="a8474-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8474-104">方法</span><span class="sxs-lookup"><span data-stu-id="a8474-104">Methods</span></span>  
  
|<span data-ttu-id="a8474-105">方法</span><span class="sxs-lookup"><span data-stu-id="a8474-105">Method</span></span>|<span data-ttu-id="a8474-106">描述</span><span class="sxs-lookup"><span data-stu-id="a8474-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8474-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="a8474-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="a8474-108">從列舉中取得指定`ICorDebugModule`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="a8474-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8474-109">備註</span><span class="sxs-lookup"><span data-stu-id="a8474-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8474-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a8474-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8474-111">需求</span><span class="sxs-lookup"><span data-stu-id="a8474-111">Requirements</span></span>  
 <span data-ttu-id="a8474-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8474-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8474-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8474-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8474-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8474-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8474-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8474-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8474-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8474-116">See also</span></span>

- [<span data-ttu-id="a8474-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a8474-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

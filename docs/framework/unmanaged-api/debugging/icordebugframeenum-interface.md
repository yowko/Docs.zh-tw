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
ms.openlocfilehash: cd24dfa6771ca450e79b4b932735968ecc51fc90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093814"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="c912d-102">ICorDebugFrameEnum 介面</span><span class="sxs-lookup"><span data-stu-id="c912d-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="c912d-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugFrame 陣列。</span><span class="sxs-lookup"><span data-stu-id="c912d-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c912d-104">方法</span><span class="sxs-lookup"><span data-stu-id="c912d-104">Methods</span></span>  
  
|<span data-ttu-id="c912d-105">方法</span><span class="sxs-lookup"><span data-stu-id="c912d-105">Method</span></span>|<span data-ttu-id="c912d-106">描述</span><span class="sxs-lookup"><span data-stu-id="c912d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c912d-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="c912d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="c912d-108">取得指定的數目`ICorDebugFrame`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c912d-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c912d-109">備註</span><span class="sxs-lookup"><span data-stu-id="c912d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c912d-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c912d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c912d-111">需求</span><span class="sxs-lookup"><span data-stu-id="c912d-111">Requirements</span></span>  
 <span data-ttu-id="c912d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c912d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c912d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c912d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c912d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c912d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c912d-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c912d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c912d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c912d-116">See also</span></span>

- [<span data-ttu-id="c912d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c912d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

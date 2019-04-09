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
ms.openlocfilehash: 26efb3e43642b6d1fd10b084c2b321609c89d89b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146506"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="e58d8-102">ICorDebugModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e58d8-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="e58d8-103">實作 ICorDebugEnum 方法，並列舉 ICorDebugModule 陣列。</span><span class="sxs-lookup"><span data-stu-id="e58d8-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e58d8-104">方法</span><span class="sxs-lookup"><span data-stu-id="e58d8-104">Methods</span></span>  
  
|<span data-ttu-id="e58d8-105">方法</span><span class="sxs-lookup"><span data-stu-id="e58d8-105">Method</span></span>|<span data-ttu-id="e58d8-106">描述</span><span class="sxs-lookup"><span data-stu-id="e58d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e58d8-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="e58d8-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="e58d8-108">取得指定的數目`ICorDebugModule`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e58d8-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e58d8-109">備註</span><span class="sxs-lookup"><span data-stu-id="e58d8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e58d8-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e58d8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e58d8-111">需求</span><span class="sxs-lookup"><span data-stu-id="e58d8-111">Requirements</span></span>  
 <span data-ttu-id="e58d8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e58d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e58d8-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e58d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e58d8-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e58d8-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e58d8-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e58d8-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e58d8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e58d8-116">See also</span></span>

- [<span data-ttu-id="e58d8-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e58d8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

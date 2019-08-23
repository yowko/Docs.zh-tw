---
title: ICorDebugTypeEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum
helpviewer_keywords:
- ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: 159ccfcf-b37c-4ad9-8e0d-a9a443262472
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b81230ee901510b2859b45de76c6dcfa6cb28e58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968189"
---
# <a name="icordebugtypeenum-interface"></a><span data-ttu-id="dfcac-102">ICorDebugTypeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dfcac-102">ICorDebugTypeEnum Interface</span></span>
<span data-ttu-id="dfcac-103">會執行 "ICorDebugEnum" 方法, 並列舉 "ICorDebugType" 陣列。</span><span class="sxs-lookup"><span data-stu-id="dfcac-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugType" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dfcac-104">方法</span><span class="sxs-lookup"><span data-stu-id="dfcac-104">Methods</span></span>  
  
|<span data-ttu-id="dfcac-105">方法</span><span class="sxs-lookup"><span data-stu-id="dfcac-105">Method</span></span>|<span data-ttu-id="dfcac-106">描述</span><span class="sxs-lookup"><span data-stu-id="dfcac-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfcac-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="dfcac-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-next-method.md)|<span data-ttu-id="dfcac-108">從列舉中取得指定`ICorDebugType`的實例數目, 從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="dfcac-108">Gets the specified number of `ICorDebugType` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfcac-109">備註</span><span class="sxs-lookup"><span data-stu-id="dfcac-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfcac-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="dfcac-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfcac-111">需求</span><span class="sxs-lookup"><span data-stu-id="dfcac-111">Requirements</span></span>  
 <span data-ttu-id="dfcac-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfcac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfcac-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dfcac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfcac-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dfcac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfcac-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfcac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfcac-116">See also</span></span>

- [<span data-ttu-id="dfcac-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="dfcac-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: 6f36ce2fbf57c72102550069989c94b5cc19e58c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186650"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="3761d-102">ICorDebugCodeEnum 介面</span><span class="sxs-lookup"><span data-stu-id="3761d-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="3761d-103">實作 「 ICorDebugEnum 」 方法，並列舉"ICorDebugCode"陣列。</span><span class="sxs-lookup"><span data-stu-id="3761d-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3761d-104">方法</span><span class="sxs-lookup"><span data-stu-id="3761d-104">Methods</span></span>  
  
|<span data-ttu-id="3761d-105">方法</span><span class="sxs-lookup"><span data-stu-id="3761d-105">Method</span></span>|<span data-ttu-id="3761d-106">描述</span><span class="sxs-lookup"><span data-stu-id="3761d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3761d-107">Next 方法</span><span class="sxs-lookup"><span data-stu-id="3761d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-next-method.md)|<span data-ttu-id="3761d-108">取得指定的數目`ICorDebugCode`從列舉型別，從目前位置開始的執行個體。</span><span class="sxs-lookup"><span data-stu-id="3761d-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3761d-109">備註</span><span class="sxs-lookup"><span data-stu-id="3761d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3761d-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="3761d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3761d-111">需求</span><span class="sxs-lookup"><span data-stu-id="3761d-111">Requirements</span></span>  
 <span data-ttu-id="3761d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3761d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3761d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3761d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3761d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3761d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3761d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3761d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3761d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3761d-116">See also</span></span>

- [<span data-ttu-id="3761d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3761d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugBlockingObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11693416d0a3e0afe80c2356ff0a12ecea0d8d15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959304"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="abe68-102">ICorDebugBlockingObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="abe68-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="abe68-103">提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構清單的列舉值。</span><span class="sxs-lookup"><span data-stu-id="abe68-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="abe68-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="abe68-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abe68-105">方法</span><span class="sxs-lookup"><span data-stu-id="abe68-105">Methods</span></span>  
  
|<span data-ttu-id="abe68-106">方法</span><span class="sxs-lookup"><span data-stu-id="abe68-106">Method</span></span>|<span data-ttu-id="abe68-107">描述</span><span class="sxs-lookup"><span data-stu-id="abe68-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abe68-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="abe68-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="abe68-109">列舉[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構的清單。</span><span class="sxs-lookup"><span data-stu-id="abe68-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abe68-110">備註</span><span class="sxs-lookup"><span data-stu-id="abe68-110">Remarks</span></span>  
 <span data-ttu-id="abe68-111">每個 `CorDebugBlockingObject` 結構各代表一個封鎖執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="abe68-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abe68-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="abe68-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe68-113">需求</span><span class="sxs-lookup"><span data-stu-id="abe68-113">Requirements</span></span>  
 <span data-ttu-id="abe68-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abe68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe68-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abe68-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abe68-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe68-117">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe68-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abe68-118">See also</span></span>

- [<span data-ttu-id="abe68-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="abe68-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="abe68-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="abe68-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

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
ms.openlocfilehash: f22d9d86e2b943a8825e1ec271a401b03f73fb6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407010"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="d0a9a-102">ICorDebugBlockingObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d0a9a-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="d0a9a-103">提供列舉值的清單[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="d0a9a-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="d0a9a-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="d0a9a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0a9a-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0a9a-105">Methods</span></span>  
  
|<span data-ttu-id="d0a9a-106">方法</span><span class="sxs-lookup"><span data-stu-id="d0a9a-106">Method</span></span>|<span data-ttu-id="d0a9a-107">描述</span><span class="sxs-lookup"><span data-stu-id="d0a9a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0a9a-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="d0a9a-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="d0a9a-109">透過清單列舉[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="d0a9a-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0a9a-110">備註</span><span class="sxs-lookup"><span data-stu-id="d0a9a-110">Remarks</span></span>  
 <span data-ttu-id="d0a9a-111">每個 `CorDebugBlockingObject` 結構各代表一個封鎖執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="d0a9a-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0a9a-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0a9a-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a9a-113">需求</span><span class="sxs-lookup"><span data-stu-id="d0a9a-113">Requirements</span></span>  
 <span data-ttu-id="d0a9a-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a9a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0a9a-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0a9a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0a9a-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0a9a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0a9a-117">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0a9a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a9a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a9a-118">See Also</span></span>  
 [<span data-ttu-id="d0a9a-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d0a9a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d0a9a-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="d0a9a-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

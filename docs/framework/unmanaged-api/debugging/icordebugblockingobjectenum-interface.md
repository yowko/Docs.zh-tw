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
ms.openlocfilehash: 5a23d21d0ed8c6a6a226d5e58eafb7bde65a4896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645431"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="a62d3-102">ICorDebugBlockingObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a62d3-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="a62d3-103">提供列舉值，取得一份[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="a62d3-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="a62d3-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="a62d3-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a62d3-105">方法</span><span class="sxs-lookup"><span data-stu-id="a62d3-105">Methods</span></span>  
  
|<span data-ttu-id="a62d3-106">方法</span><span class="sxs-lookup"><span data-stu-id="a62d3-106">Method</span></span>|<span data-ttu-id="a62d3-107">描述</span><span class="sxs-lookup"><span data-stu-id="a62d3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a62d3-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="a62d3-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="a62d3-109">列舉的清單[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="a62d3-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a62d3-110">備註</span><span class="sxs-lookup"><span data-stu-id="a62d3-110">Remarks</span></span>  
 <span data-ttu-id="a62d3-111">每個 `CorDebugBlockingObject` 結構各代表一個封鎖執行緒的物件。</span><span class="sxs-lookup"><span data-stu-id="a62d3-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a62d3-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a62d3-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a62d3-113">需求</span><span class="sxs-lookup"><span data-stu-id="a62d3-113">Requirements</span></span>  
 <span data-ttu-id="a62d3-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a62d3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62d3-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a62d3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a62d3-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a62d3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a62d3-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62d3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62d3-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a62d3-118">See also</span></span>

- [<span data-ttu-id="a62d3-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a62d3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a62d3-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="a62d3-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugManagedCallback3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acab49097059081540ec364d7f134d31432988a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108273"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="c9aaa-102">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="c9aaa-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="c9aaa-103">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="c9aaa-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9aaa-104">方法</span><span class="sxs-lookup"><span data-stu-id="c9aaa-104">Methods</span></span>  
  
|<span data-ttu-id="c9aaa-105">方法</span><span class="sxs-lookup"><span data-stu-id="c9aaa-105">Method</span></span>|<span data-ttu-id="c9aaa-106">描述</span><span class="sxs-lookup"><span data-stu-id="c9aaa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9aaa-107">CustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="c9aaa-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="c9aaa-108">表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="c9aaa-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9aaa-109">備註</span><span class="sxs-lookup"><span data-stu-id="c9aaa-109">Remarks</span></span>  
 <span data-ttu-id="c9aaa-110">這個介面是的邏輯擴充[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)並[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c9aaa-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9aaa-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c9aaa-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9aaa-112">需求</span><span class="sxs-lookup"><span data-stu-id="c9aaa-112">Requirements</span></span>  
 <span data-ttu-id="c9aaa-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9aaa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9aaa-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9aaa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9aaa-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9aaa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9aaa-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9aaa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9aaa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9aaa-117">See also</span></span>

- [<span data-ttu-id="c9aaa-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c9aaa-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="c9aaa-119">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="c9aaa-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="c9aaa-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c9aaa-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c9aaa-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="c9aaa-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugThread4 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d66a1aed1936d0146d42c8e4a5ad06dfa39c802
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962968"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="0a5fe-102">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="0a5fe-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="0a5fe-103">提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a5fe-104">方法</span><span class="sxs-lookup"><span data-stu-id="0a5fe-104">Methods</span></span>  
  
|<span data-ttu-id="0a5fe-105">方法</span><span class="sxs-lookup"><span data-stu-id="0a5fe-105">Method</span></span>|<span data-ttu-id="0a5fe-106">描述</span><span class="sxs-lookup"><span data-stu-id="0a5fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a5fe-107">GetBlockingObjects 方法</span><span class="sxs-lookup"><span data-stu-id="0a5fe-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="0a5fe-108">提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構的已排序列舉, 以提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="0a5fe-109">HadUnhandledException 方法</span><span class="sxs-lookup"><span data-stu-id="0a5fe-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="0a5fe-110">指出執行緒是否曾經有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="0a5fe-111">GetCurrentCustomDebuggerNotification 方法</span><span class="sxs-lookup"><span data-stu-id="0a5fe-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="0a5fe-112">取得目前線程上的目前[ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)物件。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a5fe-113">備註</span><span class="sxs-lookup"><span data-stu-id="0a5fe-113">Remarks</span></span>  
 <span data-ttu-id="0a5fe-114">這個介面是 ICorDebugThread、ICorDebugThread2 和[ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a5fe-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a5fe-116">需求</span><span class="sxs-lookup"><span data-stu-id="0a5fe-116">Requirements</span></span>  
 <span data-ttu-id="0a5fe-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a5fe-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a5fe-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a5fe-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a5fe-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a5fe-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a5fe-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a5fe-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a5fe-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a5fe-121">See also</span></span>

- [<span data-ttu-id="0a5fe-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0a5fe-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0a5fe-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="0a5fe-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

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
ms.openlocfilehash: cf486be306e149e2350e7239884c8f05b84f3a86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422080"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="e9a42-102">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="e9a42-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="e9a42-103">提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="e9a42-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9a42-104">方法</span><span class="sxs-lookup"><span data-stu-id="e9a42-104">Methods</span></span>  
  
|<span data-ttu-id="e9a42-105">方法</span><span class="sxs-lookup"><span data-stu-id="e9a42-105">Method</span></span>|<span data-ttu-id="e9a42-106">描述</span><span class="sxs-lookup"><span data-stu-id="e9a42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9a42-107">GetBlockingObjects 方法</span><span class="sxs-lookup"><span data-stu-id="e9a42-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="e9a42-108">提供的已排序的列舉[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="e9a42-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="e9a42-109">HadUnhandledException 方法</span><span class="sxs-lookup"><span data-stu-id="e9a42-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="e9a42-110">指出執行緒是否有曾經處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e9a42-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="e9a42-111">GetCurrentCustomDebuggerNotification 方法</span><span class="sxs-lookup"><span data-stu-id="e9a42-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="e9a42-112">取得目前[icordebugmanagedcallback3:: Customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)目前執行緒上的物件。</span><span class="sxs-lookup"><span data-stu-id="e9a42-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a42-113">備註</span><span class="sxs-lookup"><span data-stu-id="e9a42-113">Remarks</span></span>  
 <span data-ttu-id="e9a42-114">這個介面是 ICorDebugThread，ICorDebugThread2 的邏輯擴充功能和[ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e9a42-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9a42-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e9a42-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a42-116">需求</span><span class="sxs-lookup"><span data-stu-id="e9a42-116">Requirements</span></span>  
 <span data-ttu-id="e9a42-117">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9a42-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a42-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9a42-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9a42-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9a42-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9a42-120">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a42-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a42-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9a42-121">See Also</span></span>  
 [<span data-ttu-id="e9a42-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e9a42-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e9a42-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="e9a42-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

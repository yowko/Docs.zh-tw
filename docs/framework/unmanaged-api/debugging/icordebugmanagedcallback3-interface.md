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
ms.openlocfilehash: 63e3f166c4cbf17f4892dccf770343bfbf6e0284
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209743"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="f420a-102">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="f420a-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="f420a-103">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="f420a-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f420a-104">方法</span><span class="sxs-lookup"><span data-stu-id="f420a-104">Methods</span></span>  
  
|<span data-ttu-id="f420a-105">方法</span><span class="sxs-lookup"><span data-stu-id="f420a-105">Method</span></span>|<span data-ttu-id="f420a-106">描述</span><span class="sxs-lookup"><span data-stu-id="f420a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f420a-107">CustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="f420a-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="f420a-108">表示已引發已啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="f420a-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f420a-109">備註</span><span class="sxs-lookup"><span data-stu-id="f420a-109">Remarks</span></span>  
 <span data-ttu-id="f420a-110">這個介面是[ICorDebugManagedCallback](icordebugmanagedcallback-interface.md)和[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="f420a-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f420a-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f420a-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f420a-112">需求</span><span class="sxs-lookup"><span data-stu-id="f420a-112">Requirements</span></span>  
 <span data-ttu-id="f420a-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f420a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f420a-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f420a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f420a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f420a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f420a-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f420a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f420a-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="f420a-117">See also</span></span>

- [<span data-ttu-id="f420a-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f420a-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="f420a-119">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="f420a-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f420a-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f420a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f420a-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="f420a-121">Debugging</span></span>](index.md)

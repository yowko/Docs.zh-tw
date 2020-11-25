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
ms.openlocfilehash: e04f5be6d2612b26bf7d71807753d170e6a5a7a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723294"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="f2285-102">ICorDebugManagedCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="f2285-102">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="f2285-103">提供回呼方法，表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="f2285-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2285-104">方法</span><span class="sxs-lookup"><span data-stu-id="f2285-104">Methods</span></span>  
  
|<span data-ttu-id="f2285-105">方法</span><span class="sxs-lookup"><span data-stu-id="f2285-105">Method</span></span>|<span data-ttu-id="f2285-106">描述</span><span class="sxs-lookup"><span data-stu-id="f2285-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2285-107">CustomNotification 方法</span><span class="sxs-lookup"><span data-stu-id="f2285-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="f2285-108">表示已引發啟用的自訂偵錯工具通知。</span><span class="sxs-lookup"><span data-stu-id="f2285-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2285-109">備註</span><span class="sxs-lookup"><span data-stu-id="f2285-109">Remarks</span></span>  

 <span data-ttu-id="f2285-110">此介面是 [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) 和 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="f2285-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2285-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="f2285-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2285-112">需求</span><span class="sxs-lookup"><span data-stu-id="f2285-112">Requirements</span></span>  

 <span data-ttu-id="f2285-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f2285-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2285-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2285-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2285-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2285-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2285-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2285-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2285-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2285-117">See also</span></span>

- [<span data-ttu-id="f2285-118">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f2285-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="f2285-119">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="f2285-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="f2285-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f2285-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f2285-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="f2285-121">Debugging</span></span>](index.md)

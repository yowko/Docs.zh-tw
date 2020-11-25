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
ms.openlocfilehash: 5c108420772be9e6d0932f3759f18da9446f99d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727935"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="38ac8-102">ICorDebugThread4 介面</span><span class="sxs-lookup"><span data-stu-id="38ac8-102">ICorDebugThread4 Interface</span></span>

<span data-ttu-id="38ac8-103">提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="38ac8-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38ac8-104">方法</span><span class="sxs-lookup"><span data-stu-id="38ac8-104">Methods</span></span>  
  
|<span data-ttu-id="38ac8-105">方法</span><span class="sxs-lookup"><span data-stu-id="38ac8-105">Method</span></span>|<span data-ttu-id="38ac8-106">描述</span><span class="sxs-lookup"><span data-stu-id="38ac8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38ac8-107">GetBlockingObjects 方法</span><span class="sxs-lookup"><span data-stu-id="38ac8-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="38ac8-108">提供 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 結構的已排序列舉，以提供執行緒封鎖資訊。</span><span class="sxs-lookup"><span data-stu-id="38ac8-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="38ac8-109">HadUnhandledException 方法</span><span class="sxs-lookup"><span data-stu-id="38ac8-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="38ac8-110">指出執行緒是否曾經有未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="38ac8-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="38ac8-111">GetCurrentCustomDebuggerNotification 方法</span><span class="sxs-lookup"><span data-stu-id="38ac8-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="38ac8-112">取得目前線程上目前的 [ICorDebugManagedCallback3：： CustomNotification](icordebugmanagedcallback3-customnotification-method.md) 物件。</span><span class="sxs-lookup"><span data-stu-id="38ac8-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38ac8-113">備註</span><span class="sxs-lookup"><span data-stu-id="38ac8-113">Remarks</span></span>  

 <span data-ttu-id="38ac8-114">此介面是 ICorDebugThread、ICorDebugThread2 和 [ICorDebugThread3](icordebugthread3-interface.md) 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="38ac8-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38ac8-115">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="38ac8-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38ac8-116">需求</span><span class="sxs-lookup"><span data-stu-id="38ac8-116">Requirements</span></span>  

 <span data-ttu-id="38ac8-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38ac8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38ac8-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38ac8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38ac8-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38ac8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38ac8-120">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38ac8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ac8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38ac8-121">See also</span></span>

- [<span data-ttu-id="38ac8-122">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="38ac8-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="38ac8-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="38ac8-123">Debugging</span></span>](index.md)

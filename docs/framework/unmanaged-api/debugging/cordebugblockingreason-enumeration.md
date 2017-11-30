---
title: "CorDebugBlockingReason 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingReason
helpviewer_keywords: CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 505a83f15d5056b0280af31d372623530d6e66ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="0a1fa-102">CorDebugBlockingReason 列舉</span><span class="sxs-lookup"><span data-stu-id="0a1fa-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="0a1fa-103">指定給定物件上封鎖執行緒的原因。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a1fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a1fa-104">Syntax</span></span>  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="0a1fa-105">成員</span><span class="sxs-lookup"><span data-stu-id="0a1fa-105">Members</span></span>  
  
|<span data-ttu-id="0a1fa-106">成員</span><span class="sxs-lookup"><span data-stu-id="0a1fa-106">Member</span></span>|<span data-ttu-id="0a1fa-107">說明</span><span class="sxs-lookup"><span data-stu-id="0a1fa-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="0a1fa-108">僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="0a1fa-109">執行緒嘗試取得監視器鎖定物件相關聯的重要區段。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="0a1fa-110">通常，發生這種情況時您呼叫其中一個<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>或<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="0a1fa-111">執行緒正在等候物件監視器鎖定相關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="0a1fa-112">通常，發生這種情況時您呼叫其中一個<xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait`方法。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a1fa-113">備註</span><span class="sxs-lookup"><span data-stu-id="0a1fa-113">Remarks</span></span>  
 <span data-ttu-id="0a1fa-114">當`BLOCKING_MONITOR_CRITICAL_SECTION`或`BLOCKING_MONITOR_EVENT`成員用於[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構`pBlockingObject`"ICorDebugValue 」 介面，表示正在輸入的物件指向的結構的成員.</span><span class="sxs-lookup"><span data-stu-id="0a1fa-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="0a1fa-115">它也保證實作[ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a1fa-116">需求</span><span class="sxs-lookup"><span data-stu-id="0a1fa-116">Requirements</span></span>  
 <span data-ttu-id="0a1fa-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a1fa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a1fa-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a1fa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a1fa-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a1fa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a1fa-120">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a1fa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a1fa-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a1fa-121">See Also</span></span>  
 [<span data-ttu-id="0a1fa-122">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="0a1fa-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="0a1fa-123">偵錯</span><span class="sxs-lookup"><span data-stu-id="0a1fa-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

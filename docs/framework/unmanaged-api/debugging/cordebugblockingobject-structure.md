---
title: "CorDebugBlockingObject 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingObject Structure
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingObject
helpviewer_keywords: CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c47735565c960c2600f7274d0d59d5a6ec6c178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="11d40-102">CorDebugBlockingObject 結構</span><span class="sxs-lookup"><span data-stu-id="11d40-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="11d40-103">定義為以及封鎖執行緒的執行緒會封鎖的特定原因的物件。</span><span class="sxs-lookup"><span data-stu-id="11d40-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d40-104">語法</span><span class="sxs-lookup"><span data-stu-id="11d40-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="11d40-105">成員</span><span class="sxs-lookup"><span data-stu-id="11d40-105">Members</span></span>  
  
|<span data-ttu-id="11d40-106">成員</span><span class="sxs-lookup"><span data-stu-id="11d40-106">Member</span></span>|<span data-ttu-id="11d40-107">說明</span><span class="sxs-lookup"><span data-stu-id="11d40-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="11d40-108">物件所在的執行緒會封鎖。</span><span class="sxs-lookup"><span data-stu-id="11d40-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="11d40-109">僅針對目前已同步處理狀態的持續時間，這個物件是有效的。</span><span class="sxs-lookup"><span data-stu-id="11d40-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="11d40-110">如果兩個執行緒會封鎖在相同的已同步處理狀態中相同的物件上，您可能預期[icordebugvalue:: Getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)方法以傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="11d40-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="11d40-111">不過，介面可能會或可能不是對等的指標。</span><span class="sxs-lookup"><span data-stu-id="11d40-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="11d40-112">逾時或無限，表示它將會逾時的值，將會封鎖作業之前的毫秒數。逾時值指定的總時間封鎖作業，而不是仍在剩餘的時間長度。</span><span class="sxs-lookup"><span data-stu-id="11d40-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="11d40-113">執行緒已在此物件上封鎖原因。</span><span class="sxs-lookup"><span data-stu-id="11d40-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11d40-114">備註</span><span class="sxs-lookup"><span data-stu-id="11d40-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d40-115">需求</span><span class="sxs-lookup"><span data-stu-id="11d40-115">Requirements</span></span>  
 <span data-ttu-id="11d40-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11d40-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d40-117">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="11d40-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="11d40-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11d40-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11d40-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11d40-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d40-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11d40-120">See Also</span></span>  
 [<span data-ttu-id="11d40-121">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="11d40-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="11d40-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="11d40-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

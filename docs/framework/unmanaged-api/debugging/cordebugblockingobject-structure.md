---
title: CorDebugBlockingObject 結構
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83dac3b9b2ac396cdef19695fcce0f7e20485a50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740402"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="7f43b-102">CorDebugBlockingObject 結構</span><span class="sxs-lookup"><span data-stu-id="7f43b-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="7f43b-103">定義封鎖執行緒和執行緒已封鎖的特定原因的物件。</span><span class="sxs-lookup"><span data-stu-id="7f43b-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f43b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f43b-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="7f43b-105">成員</span><span class="sxs-lookup"><span data-stu-id="7f43b-105">Members</span></span>  
  
|<span data-ttu-id="7f43b-106">成員</span><span class="sxs-lookup"><span data-stu-id="7f43b-106">Member</span></span>|<span data-ttu-id="7f43b-107">描述</span><span class="sxs-lookup"><span data-stu-id="7f43b-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="7f43b-108">物件，在其封鎖執行緒。</span><span class="sxs-lookup"><span data-stu-id="7f43b-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="7f43b-109">這個物件是有效的只會針對目前的同步處理狀態的持續時間。</span><span class="sxs-lookup"><span data-stu-id="7f43b-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="7f43b-110">如果兩個執行緒會封鎖相同的同步處理狀態中的相同物件上，您可能會預期[icordebugvalue:: Getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)方法來傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="7f43b-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="7f43b-111">不過，介面可能會或可能不到對等的指標。</span><span class="sxs-lookup"><span data-stu-id="7f43b-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="7f43b-112">逾時或值為 INFINITE，這表示它將會逾時，將會封鎖作業之前的毫秒數。逾時值指定時間的封鎖作業，也就是不是仍剩餘的時間總長度。</span><span class="sxs-lookup"><span data-stu-id="7f43b-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="7f43b-113">執行緒已封鎖此物件上的原因。</span><span class="sxs-lookup"><span data-stu-id="7f43b-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f43b-114">備註</span><span class="sxs-lookup"><span data-stu-id="7f43b-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f43b-115">需求</span><span class="sxs-lookup"><span data-stu-id="7f43b-115">Requirements</span></span>  
 <span data-ttu-id="7f43b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f43b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f43b-117">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="7f43b-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="7f43b-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f43b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f43b-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f43b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f43b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f43b-120">See also</span></span>

- [<span data-ttu-id="7f43b-121">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="7f43b-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="7f43b-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="7f43b-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

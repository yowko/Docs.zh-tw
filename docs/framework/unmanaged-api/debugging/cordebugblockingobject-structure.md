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
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273962"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="0cd51-102">CorDebugBlockingObject 結構</span><span class="sxs-lookup"><span data-stu-id="0cd51-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="0cd51-103">定義封鎖執行緒的物件，以及執行緒遭到封鎖的特定原因。</span><span class="sxs-lookup"><span data-stu-id="0cd51-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cd51-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cd51-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="0cd51-105">成員</span><span class="sxs-lookup"><span data-stu-id="0cd51-105">Members</span></span>  
  
|<span data-ttu-id="0cd51-106">成員</span><span class="sxs-lookup"><span data-stu-id="0cd51-106">Member</span></span>|<span data-ttu-id="0cd51-107">描述</span><span class="sxs-lookup"><span data-stu-id="0cd51-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="0cd51-108">執行緒封鎖所在的物件。</span><span class="sxs-lookup"><span data-stu-id="0cd51-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="0cd51-109">這個物件只在目前已同步處理狀態的持續時間內有效。</span><span class="sxs-lookup"><span data-stu-id="0cd51-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="0cd51-110">如果兩個執行緒在相同物件的已同步處理狀態下封鎖，您可能會預期[ICorDebugValue：： GetAddress](icordebugvalue-getaddress-method.md)方法傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="0cd51-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="0cd51-111">不過，介面不一定是對等的指標。</span><span class="sxs-lookup"><span data-stu-id="0cd51-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="0cd51-112">封鎖作業超時前的毫秒數，或無限值，表示不會超時。超時值會指定封鎖作業的總時間長度，而不是仍然剩餘的時間。</span><span class="sxs-lookup"><span data-stu-id="0cd51-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="0cd51-113">此物件上封鎖執行緒的原因。</span><span class="sxs-lookup"><span data-stu-id="0cd51-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cd51-114">備註</span><span class="sxs-lookup"><span data-stu-id="0cd51-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cd51-115">需求</span><span class="sxs-lookup"><span data-stu-id="0cd51-115">Requirements</span></span>  
 <span data-ttu-id="0cd51-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cd51-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cd51-117">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="0cd51-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="0cd51-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cd51-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cd51-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cd51-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd51-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd51-120">See also</span></span>

- [<span data-ttu-id="0cd51-121">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="0cd51-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0cd51-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="0cd51-122">Debugging</span></span>](index.md)

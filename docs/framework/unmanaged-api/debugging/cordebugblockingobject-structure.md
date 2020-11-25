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
ms.openlocfilehash: b16feb1af0d4975411876e78940d21096750d2ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726581"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="572d7-102">CorDebugBlockingObject 結構</span><span class="sxs-lookup"><span data-stu-id="572d7-102">CorDebugBlockingObject Structure</span></span>

<span data-ttu-id="572d7-103">定義封鎖執行緒的物件，以及封鎖執行緒的特定原因。</span><span class="sxs-lookup"><span data-stu-id="572d7-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="572d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="572d7-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="572d7-105">成員</span><span class="sxs-lookup"><span data-stu-id="572d7-105">Members</span></span>  
  
|<span data-ttu-id="572d7-106">member</span><span class="sxs-lookup"><span data-stu-id="572d7-106">Member</span></span>|<span data-ttu-id="572d7-107">描述</span><span class="sxs-lookup"><span data-stu-id="572d7-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="572d7-108">執行緒封鎖所在的物件。</span><span class="sxs-lookup"><span data-stu-id="572d7-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="572d7-109">只有在目前已同步處理狀態的持續時間內，此物件才有效。</span><span class="sxs-lookup"><span data-stu-id="572d7-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="572d7-110">如果兩個執行緒在相同物件的相同同步處理狀態中封鎖，您可能會預期 [ICorDebugValue：： GetAddress](icordebugvalue-getaddress-method.md) 方法會傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="572d7-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="572d7-111">不過，介面可能會或可能不是指標相等。</span><span class="sxs-lookup"><span data-stu-id="572d7-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="572d7-112">封鎖作業超時之前的毫秒數，或值無限，表示不會超時。超時值指定封鎖作業的總時間長度，而不是剩餘的時間。</span><span class="sxs-lookup"><span data-stu-id="572d7-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="572d7-113">此物件封鎖執行緒的原因。</span><span class="sxs-lookup"><span data-stu-id="572d7-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="572d7-114">備註</span><span class="sxs-lookup"><span data-stu-id="572d7-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="572d7-115">需求</span><span class="sxs-lookup"><span data-stu-id="572d7-115">Requirements</span></span>  

 <span data-ttu-id="572d7-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="572d7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="572d7-117">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="572d7-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="572d7-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="572d7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="572d7-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="572d7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572d7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="572d7-120">See also</span></span>

- [<span data-ttu-id="572d7-121">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="572d7-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="572d7-122">偵錯</span><span class="sxs-lookup"><span data-stu-id="572d7-122">Debugging</span></span>](index.md)

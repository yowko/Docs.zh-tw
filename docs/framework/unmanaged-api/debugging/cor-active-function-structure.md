---
title: COR_ACTIVE_FUNCTION 結構
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd4acece43628b20b6bc50a539ee197e865855
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274148"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="828b6-102">COR_ACTIVE_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="828b6-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="828b6-103">包含目前執行緒框架中正在作用的函式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="828b6-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="828b6-104">這個結構是由[ICorDebugThread2：： GetActiveFunctions](icordebugthread2-getactivefunctions-method.md)方法所使用。</span><span class="sxs-lookup"><span data-stu-id="828b6-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="828b6-105">語法</span><span class="sxs-lookup"><span data-stu-id="828b6-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="828b6-106">成員</span><span class="sxs-lookup"><span data-stu-id="828b6-106">Members</span></span>  
  
|<span data-ttu-id="828b6-107">成員</span><span class="sxs-lookup"><span data-stu-id="828b6-107">Member</span></span>|<span data-ttu-id="828b6-108">描述</span><span class="sxs-lookup"><span data-stu-id="828b6-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="828b6-109">`ilOffset`欄位之應用程式域擁有者的指標。</span><span class="sxs-lookup"><span data-stu-id="828b6-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="828b6-110">`ilOffset`欄位之模組擁有者的指標。</span><span class="sxs-lookup"><span data-stu-id="828b6-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="828b6-111">`ilOffset`欄位之函數擁有者的指標。</span><span class="sxs-lookup"><span data-stu-id="828b6-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="828b6-112">框架的 Microsoft 中繼語言（MSIL）位移。</span><span class="sxs-lookup"><span data-stu-id="828b6-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="828b6-113">保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="828b6-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="828b6-114">需求</span><span class="sxs-lookup"><span data-stu-id="828b6-114">Requirements</span></span>  
 <span data-ttu-id="828b6-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="828b6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="828b6-116">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="828b6-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="828b6-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="828b6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="828b6-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="828b6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="828b6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="828b6-119">See also</span></span>

- [<span data-ttu-id="828b6-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="828b6-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="828b6-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="828b6-121">Debugging</span></span>](index.md)

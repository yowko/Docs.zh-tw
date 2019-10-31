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
ms.openlocfilehash: cbc272070e9eb6810b34ec1f3fdc9e944c624cd3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132388"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="62580-102">COR_ACTIVE_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="62580-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="62580-103">包含目前執行緒框架中正在作用的函式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="62580-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="62580-104">這個結構是由[ICorDebugThread2：： GetActiveFunctions](icordebugthread2-getactivefunctions-method.md)方法所使用。</span><span class="sxs-lookup"><span data-stu-id="62580-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62580-105">語法</span><span class="sxs-lookup"><span data-stu-id="62580-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="62580-106">Members</span><span class="sxs-lookup"><span data-stu-id="62580-106">Members</span></span>  
  
|<span data-ttu-id="62580-107">成員</span><span class="sxs-lookup"><span data-stu-id="62580-107">Member</span></span>|<span data-ttu-id="62580-108">描述</span><span class="sxs-lookup"><span data-stu-id="62580-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="62580-109">`ilOffset` 欄位之應用程式域擁有者的指標。</span><span class="sxs-lookup"><span data-stu-id="62580-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="62580-110">`ilOffset` 欄位之模組擁有者的指標。</span><span class="sxs-lookup"><span data-stu-id="62580-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="62580-111">`ilOffset` 欄位之函式擁有者的指標。</span><span class="sxs-lookup"><span data-stu-id="62580-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="62580-112">框架的 Microsoft 中繼語言（MSIL）位移。</span><span class="sxs-lookup"><span data-stu-id="62580-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="62580-113">保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="62580-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62580-114">需求</span><span class="sxs-lookup"><span data-stu-id="62580-114">Requirements</span></span>  
 <span data-ttu-id="62580-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62580-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62580-116">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="62580-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="62580-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62580-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62580-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62580-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62580-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="62580-119">See also</span></span>

- [<span data-ttu-id="62580-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="62580-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="62580-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="62580-121">Debugging</span></span>](index.md)

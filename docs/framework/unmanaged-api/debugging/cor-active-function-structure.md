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
ms.openlocfilehash: c0400da0cd29d642a1be42be7e2b22213ae54b94
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609656"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="42f8d-102">COR_ACTIVE_FUNCTION 結構</span><span class="sxs-lookup"><span data-stu-id="42f8d-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="42f8d-103">包含目前執行緒框架中正在作用的函式相關資訊。</span><span class="sxs-lookup"><span data-stu-id="42f8d-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="42f8d-104">此結構由[ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="42f8d-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42f8d-105">語法</span><span class="sxs-lookup"><span data-stu-id="42f8d-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="42f8d-106">成員</span><span class="sxs-lookup"><span data-stu-id="42f8d-106">Members</span></span>  
  
|<span data-ttu-id="42f8d-107">成員</span><span class="sxs-lookup"><span data-stu-id="42f8d-107">Member</span></span>|<span data-ttu-id="42f8d-108">描述</span><span class="sxs-lookup"><span data-stu-id="42f8d-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="42f8d-109">應用程式網域的擁有者指標`ilOffset`欄位。</span><span class="sxs-lookup"><span data-stu-id="42f8d-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="42f8d-110">指標的模組擁有者`ilOffset`欄位。</span><span class="sxs-lookup"><span data-stu-id="42f8d-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="42f8d-111">指標的函式擁有者`ilOffset`欄位。</span><span class="sxs-lookup"><span data-stu-id="42f8d-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="42f8d-112">Microsoft intermediate language (MSIL) 位移的框架。</span><span class="sxs-lookup"><span data-stu-id="42f8d-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="42f8d-113">保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="42f8d-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42f8d-114">需求</span><span class="sxs-lookup"><span data-stu-id="42f8d-114">Requirements</span></span>  
 <span data-ttu-id="42f8d-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42f8d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42f8d-116">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="42f8d-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="42f8d-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42f8d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42f8d-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42f8d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42f8d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42f8d-119">See also</span></span>

- [<span data-ttu-id="42f8d-120">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="42f8d-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="42f8d-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="42f8d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

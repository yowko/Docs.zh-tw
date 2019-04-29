---
title: CorDebugExceptionCallbackType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91b09be04499396a2229962fd592f29cb8bc8d04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609021"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="ca1e7-102">CorDebugExceptionCallbackType 列舉</span><span class="sxs-lookup"><span data-stu-id="ca1e7-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="ca1e7-103">表示一種從進行的回呼[ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)事件。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca1e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ca1e7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="ca1e7-105">成員</span><span class="sxs-lookup"><span data-stu-id="ca1e7-105">Members</span></span>  
  
|<span data-ttu-id="ca1e7-106">成員</span><span class="sxs-lookup"><span data-stu-id="ca1e7-106">Member</span></span>|<span data-ttu-id="ca1e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="ca1e7-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="ca1e7-108">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="ca1e7-109">例外狀況結束處理序已輸入使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="ca1e7-110">結束例外狀況的處理序已找到`catch`中使用者程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="ca1e7-111">未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca1e7-112">需求</span><span class="sxs-lookup"><span data-stu-id="ca1e7-112">Requirements</span></span>  
 <span data-ttu-id="ca1e7-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ca1e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca1e7-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca1e7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca1e7-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca1e7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca1e7-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca1e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca1e7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca1e7-117">See also</span></span>

- [<span data-ttu-id="ca1e7-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ca1e7-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

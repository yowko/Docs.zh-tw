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
ms.openlocfilehash: cddcf66939a2ae7ab9e7f63a6fd61b72c56f6c7a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712725"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="60fce-102">CorDebugExceptionCallbackType 列舉</span><span class="sxs-lookup"><span data-stu-id="60fce-102">CorDebugExceptionCallbackType Enumeration</span></span>

<span data-ttu-id="60fce-103">指出從 [ICorDebugManagedCallback2：： Exception](icordebugmanagedcallback2-exception-method.md) 事件進行的回呼類型。</span><span class="sxs-lookup"><span data-stu-id="60fce-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60fce-104">語法</span><span class="sxs-lookup"><span data-stu-id="60fce-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="60fce-105">成員</span><span class="sxs-lookup"><span data-stu-id="60fce-105">Members</span></span>  
  
|<span data-ttu-id="60fce-106">member</span><span class="sxs-lookup"><span data-stu-id="60fce-106">Member</span></span>|<span data-ttu-id="60fce-107">描述</span><span class="sxs-lookup"><span data-stu-id="60fce-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="60fce-108">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60fce-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="60fce-109">例外狀況 windup 處理輸入的使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="60fce-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="60fce-110">例外狀況 windup 程式 `catch` 在使用者程式碼中找到區塊。</span><span class="sxs-lookup"><span data-stu-id="60fce-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="60fce-111">未處理例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60fce-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60fce-112">需求</span><span class="sxs-lookup"><span data-stu-id="60fce-112">Requirements</span></span>  

 <span data-ttu-id="60fce-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60fce-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60fce-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60fce-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60fce-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60fce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60fce-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60fce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60fce-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60fce-117">See also</span></span>

- [<span data-ttu-id="60fce-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="60fce-118">Debugging Enumerations</span></span>](debugging-enumerations.md)

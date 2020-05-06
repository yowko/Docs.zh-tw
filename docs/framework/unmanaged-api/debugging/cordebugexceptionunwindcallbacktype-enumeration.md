---
title: CorDebugExceptionUnwindCallbackType 列舉
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: 4d2be9960f8935b754791a8badd4ea98b5d54912
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795907"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="d1120-102">CorDebugExceptionUnwindCallbackType 列舉</span><span class="sxs-lookup"><span data-stu-id="d1120-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="d1120-103">指出回呼在回溯階段期間通知的事件。</span><span class="sxs-lookup"><span data-stu-id="d1120-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1120-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1120-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="d1120-105">成員</span><span class="sxs-lookup"><span data-stu-id="d1120-105">Members</span></span>  
  
|<span data-ttu-id="d1120-106">member</span><span class="sxs-lookup"><span data-stu-id="d1120-106">Member</span></span>|<span data-ttu-id="d1120-107">說明</span><span class="sxs-lookup"><span data-stu-id="d1120-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="d1120-108">回溯進程的開始。</span><span class="sxs-lookup"><span data-stu-id="d1120-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="d1120-109">攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d1120-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1120-110">需求</span><span class="sxs-lookup"><span data-stu-id="d1120-110">Requirements</span></span>  
 <span data-ttu-id="d1120-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1120-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1120-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1120-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1120-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1120-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1120-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1120-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1120-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1120-115">See also</span></span>

- [<span data-ttu-id="d1120-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="d1120-116">Debugging Enumerations</span></span>](debugging-enumerations.md)

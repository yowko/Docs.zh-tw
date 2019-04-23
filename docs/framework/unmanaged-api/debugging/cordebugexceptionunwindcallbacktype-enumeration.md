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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408e72eeaa1dac83c45488d186425f30c6043280
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155619"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="4ce32-102">CorDebugExceptionUnwindCallbackType 列舉</span><span class="sxs-lookup"><span data-stu-id="4ce32-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="4ce32-103">指出回呼在回溯階段期間通知的事件。</span><span class="sxs-lookup"><span data-stu-id="4ce32-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce32-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ce32-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="4ce32-105">成員</span><span class="sxs-lookup"><span data-stu-id="4ce32-105">Members</span></span>  
  
|<span data-ttu-id="4ce32-106">成員</span><span class="sxs-lookup"><span data-stu-id="4ce32-106">Member</span></span>|<span data-ttu-id="4ce32-107">描述</span><span class="sxs-lookup"><span data-stu-id="4ce32-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="4ce32-108">回溯程序的開頭。</span><span class="sxs-lookup"><span data-stu-id="4ce32-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="4ce32-109">攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4ce32-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ce32-110">需求</span><span class="sxs-lookup"><span data-stu-id="4ce32-110">Requirements</span></span>  
 <span data-ttu-id="4ce32-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ce32-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ce32-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ce32-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ce32-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ce32-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ce32-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ce32-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce32-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ce32-115">See also</span></span>

- [<span data-ttu-id="4ce32-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="4ce32-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

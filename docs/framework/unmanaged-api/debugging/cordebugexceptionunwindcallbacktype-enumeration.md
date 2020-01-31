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
ms.openlocfilehash: e714c41812c8aaccd713115712df05744cc015e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789391"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="4ae50-102">CorDebugExceptionUnwindCallbackType 列舉</span><span class="sxs-lookup"><span data-stu-id="4ae50-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="4ae50-103">指出回呼在回溯階段期間通知的事件。</span><span class="sxs-lookup"><span data-stu-id="4ae50-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae50-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ae50-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="4ae50-105">Members</span><span class="sxs-lookup"><span data-stu-id="4ae50-105">Members</span></span>  
  
|<span data-ttu-id="4ae50-106">成員</span><span class="sxs-lookup"><span data-stu-id="4ae50-106">Member</span></span>|<span data-ttu-id="4ae50-107">描述</span><span class="sxs-lookup"><span data-stu-id="4ae50-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="4ae50-108">回溯進程的開始。</span><span class="sxs-lookup"><span data-stu-id="4ae50-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="4ae50-109">攔截到例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4ae50-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ae50-110">需求</span><span class="sxs-lookup"><span data-stu-id="4ae50-110">Requirements</span></span>  
 <span data-ttu-id="4ae50-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ae50-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae50-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ae50-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ae50-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ae50-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ae50-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae50-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae50-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="4ae50-115">See also</span></span>

- [<span data-ttu-id="4ae50-116">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="4ae50-116">Debugging Enumerations</span></span>](debugging-enumerations.md)

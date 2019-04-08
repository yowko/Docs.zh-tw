---
title: LogSwitchCallReason 列舉
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eadb595eb62b4f1a9dcc888225cbb7454119c7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198487"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="6457c-102">LogSwitchCallReason 列舉</span><span class="sxs-lookup"><span data-stu-id="6457c-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="6457c-103">指出在切換偵錯/追蹤時所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="6457c-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6457c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6457c-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="6457c-105">成員</span><span class="sxs-lookup"><span data-stu-id="6457c-105">Members</span></span>  
  
|<span data-ttu-id="6457c-106">成員</span><span class="sxs-lookup"><span data-stu-id="6457c-106">Member</span></span>|<span data-ttu-id="6457c-107">描述</span><span class="sxs-lookup"><span data-stu-id="6457c-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="6457c-108">建立偵錯/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="6457c-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="6457c-109">偵錯/追蹤交換器已修改。</span><span class="sxs-lookup"><span data-stu-id="6457c-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="6457c-110">偵錯/追蹤參數已被刪除。</span><span class="sxs-lookup"><span data-stu-id="6457c-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6457c-111">需求</span><span class="sxs-lookup"><span data-stu-id="6457c-111">Requirements</span></span>  
 <span data-ttu-id="6457c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6457c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6457c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6457c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6457c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6457c-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6457c-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6457c-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6457c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6457c-116">See also</span></span>

- [<span data-ttu-id="6457c-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="6457c-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

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
ms.openlocfilehash: 4d29bb3886ffb51e1dfb9654f4d70ef7c568fd43
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420704"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="c55f5-102">LogSwitchCallReason 列舉</span><span class="sxs-lookup"><span data-stu-id="c55f5-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="c55f5-103">指出在切換偵錯/追蹤時所執行的作業。</span><span class="sxs-lookup"><span data-stu-id="c55f5-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="c55f5-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="c55f5-105">成員</span><span class="sxs-lookup"><span data-stu-id="c55f5-105">Members</span></span>  
  
|<span data-ttu-id="c55f5-106">成員</span><span class="sxs-lookup"><span data-stu-id="c55f5-106">Member</span></span>|<span data-ttu-id="c55f5-107">說明</span><span class="sxs-lookup"><span data-stu-id="c55f5-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="c55f5-108">已建立偵錯工具/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="c55f5-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="c55f5-109">已修改偵錯工具/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="c55f5-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="c55f5-110">已刪除偵錯工具/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="c55f5-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c55f5-111">需求</span><span class="sxs-lookup"><span data-stu-id="c55f5-111">Requirements</span></span>  
 <span data-ttu-id="c55f5-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c55f5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c55f5-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c55f5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c55f5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c55f5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c55f5-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c55f5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55f5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c55f5-116">See also</span></span>

- [<span data-ttu-id="c55f5-117">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="c55f5-117">Debugging Enumerations</span></span>](debugging-enumerations.md)

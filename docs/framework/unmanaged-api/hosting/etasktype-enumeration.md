---
title: ETaskType 列舉
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: 332488fee4c982fdbaecceeaa2a6a3876f1602a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733694"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="30136-102">ETaskType 列舉</span><span class="sxs-lookup"><span data-stu-id="30136-102">ETaskType Enumeration</span></span>

<span data-ttu-id="30136-103">包含值，這些值表示由 [ICLRTask](iclrtask-interface.md) 或 [IHostTask](ihosttask-interface.md) 介面表示的工作類型。</span><span class="sxs-lookup"><span data-stu-id="30136-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30136-104">語法</span><span class="sxs-lookup"><span data-stu-id="30136-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="30136-105">成員</span><span class="sxs-lookup"><span data-stu-id="30136-105">Members</span></span>  
  
|<span data-ttu-id="30136-106">member</span><span class="sxs-lookup"><span data-stu-id="30136-106">Member</span></span>|<span data-ttu-id="30136-107">描述</span><span class="sxs-lookup"><span data-stu-id="30136-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="30136-108">介面代表應用程式域卸載工作。</span><span class="sxs-lookup"><span data-stu-id="30136-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="30136-109">介面代表偵錯工具 helper 工作。</span><span class="sxs-lookup"><span data-stu-id="30136-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="30136-110">介面代表完成項工作。</span><span class="sxs-lookup"><span data-stu-id="30136-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="30136-111">介面代表垃圾收集工作。</span><span class="sxs-lookup"><span data-stu-id="30136-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="30136-112">介面代表閘道執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="30136-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="30136-113">介面代表 i/o 執行緒工作或完成埠執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="30136-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="30136-114">介面代表計時器執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="30136-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="30136-115">介面代表等候執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="30136-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="30136-116">介面代表工作者執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="30136-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="30136-117">工作未知。</span><span class="sxs-lookup"><span data-stu-id="30136-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="30136-118">介面代表使用者工作。</span><span class="sxs-lookup"><span data-stu-id="30136-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30136-119">需求</span><span class="sxs-lookup"><span data-stu-id="30136-119">Requirements</span></span>  

 <span data-ttu-id="30136-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30136-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30136-121">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="30136-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30136-122">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30136-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30136-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30136-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30136-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30136-124">See also</span></span>

- [<span data-ttu-id="30136-125">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="30136-125">Hosting Enumerations</span></span>](hosting-enumerations.md)

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
ms.openlocfilehash: bc956827ad59fc655137e4147e6d98b6d097d470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138194"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="4c18c-102">ETaskType 列舉</span><span class="sxs-lookup"><span data-stu-id="4c18c-102">ETaskType Enumeration</span></span>
<span data-ttu-id="4c18c-103">包含值，表示由[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)或[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)介面代表的工作類型。</span><span class="sxs-lookup"><span data-stu-id="4c18c-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c18c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4c18c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4c18c-105">Members</span><span class="sxs-lookup"><span data-stu-id="4c18c-105">Members</span></span>  
  
|<span data-ttu-id="4c18c-106">成員</span><span class="sxs-lookup"><span data-stu-id="4c18c-106">Member</span></span>|<span data-ttu-id="4c18c-107">描述</span><span class="sxs-lookup"><span data-stu-id="4c18c-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="4c18c-108">介面代表應用程式域卸載工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="4c18c-109">介面代表偵錯工具 helper 工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="4c18c-110">介面代表完成項工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="4c18c-111">介面代表垃圾收集工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="4c18c-112">介面代表閘道執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="4c18c-113">介面代表 i/o 執行緒工作或完成通訊埠執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="4c18c-114">介面代表計時器執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="4c18c-115">介面代表等候執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="4c18c-116">介面代表工作者執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="4c18c-117">工作不明。</span><span class="sxs-lookup"><span data-stu-id="4c18c-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="4c18c-118">介面代表使用者工作。</span><span class="sxs-lookup"><span data-stu-id="4c18c-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c18c-119">需求</span><span class="sxs-lookup"><span data-stu-id="4c18c-119">Requirements</span></span>  
 <span data-ttu-id="4c18c-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c18c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c18c-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="4c18c-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c18c-122">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="4c18c-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c18c-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c18c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c18c-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="4c18c-124">See also</span></span>

- [<span data-ttu-id="4c18c-125">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="4c18c-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

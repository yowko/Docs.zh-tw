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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59fdc3d4682fe3c1967c8153043dc1bfe0668c35
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610535"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="bcb55-102">ETaskType 列舉</span><span class="sxs-lookup"><span data-stu-id="bcb55-102">ETaskType Enumeration</span></span>
<span data-ttu-id="bcb55-103">包含值，表示工作透過下列方式表示的型別[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)該[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="bcb55-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb55-104">語法</span><span class="sxs-lookup"><span data-stu-id="bcb55-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="bcb55-105">成員</span><span class="sxs-lookup"><span data-stu-id="bcb55-105">Members</span></span>  
  
|<span data-ttu-id="bcb55-106">成員</span><span class="sxs-lookup"><span data-stu-id="bcb55-106">Member</span></span>|<span data-ttu-id="bcb55-107">描述</span><span class="sxs-lookup"><span data-stu-id="bcb55-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="bcb55-108">介面代表應用程式定義域卸載的工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="bcb55-109">介面表示偵錯工具協助程式工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="bcb55-110">介面表示完成項工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="bcb55-111">介面表示記憶體回收工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="bcb55-112">介面表示閘道執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="bcb55-113">介面代表 「 I/O 執行緒的工作或完成連接埠執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="bcb55-114">介面表示計時器執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="bcb55-115">介面表示等候執行緒工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="bcb55-116">介面代表背景工作執行緒的工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="bcb55-117">未知的工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="bcb55-118">介面代表使用者的工作。</span><span class="sxs-lookup"><span data-stu-id="bcb55-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bcb55-119">需求</span><span class="sxs-lookup"><span data-stu-id="bcb55-119">Requirements</span></span>  
 <span data-ttu-id="bcb55-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bcb55-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcb55-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bcb55-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcb55-122">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bcb55-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcb55-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcb55-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb55-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcb55-124">See also</span></span>
- [<span data-ttu-id="bcb55-125">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="bcb55-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

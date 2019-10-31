---
title: ICLRTaskManager 介面
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: e25a6a03a836b8b4964b8260c974c8e8d8d9998d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092193"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="a7a95-102">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a7a95-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="a7a95-103">提供的方法可讓主機明確要求 common language runtime （CLR）建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。</span><span class="sxs-lookup"><span data-stu-id="a7a95-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7a95-104">方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-104">Methods</span></span>  
  
|<span data-ttu-id="a7a95-105">方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-105">Method</span></span>|<span data-ttu-id="a7a95-106">描述</span><span class="sxs-lookup"><span data-stu-id="a7a95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7a95-107">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="a7a95-108">明確要求 CLR 建立新的[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="a7a95-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="a7a95-109">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="a7a95-110">取得表示目前正在執行之工作的 `ICLRTask` 實例。</span><span class="sxs-lookup"><span data-stu-id="a7a95-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a7a95-111">GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="a7a95-112">取得目前正在執行之工作的型別。</span><span class="sxs-lookup"><span data-stu-id="a7a95-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="a7a95-113">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="a7a95-114">通知 CLR，主機已修改目前正在執行之工作的地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7a95-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="a7a95-115">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="a7a95-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="a7a95-116">通知 common language runtime，主機已修改目前正在執行之工作的使用者介面地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="a7a95-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7a95-117">備註</span><span class="sxs-lookup"><span data-stu-id="a7a95-117">Remarks</span></span>  
 <span data-ttu-id="a7a95-118">在主控環境中執行的每個工作都有主機端（ [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)的實例）和 CLR 端（ [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)的實例）的標記法。</span><span class="sxs-lookup"><span data-stu-id="a7a95-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="a7a95-119">主機或 CLR 可以起始工作的建立作業，但主機端標記法必須與對應的 CLR 端表示相關聯，以確保主機與 CLR 之間的工作相關成功通訊。</span><span class="sxs-lookup"><span data-stu-id="a7a95-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="a7a95-120">您必須先建立和具現化這兩個物件，然後才能在作業系統執行緒上執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a7a95-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a95-121">需求</span><span class="sxs-lookup"><span data-stu-id="a7a95-121">Requirements</span></span>  
 <span data-ttu-id="a7a95-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7a95-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a95-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a7a95-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7a95-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a7a95-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7a95-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a95-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a95-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7a95-126">See also</span></span>

- [<span data-ttu-id="a7a95-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="a7a95-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a7a95-128">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="a7a95-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a7a95-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="a7a95-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="a7a95-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="a7a95-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14c2c9b70ac2e57983ea4b16772add6a1dff5ff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438063"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="4a36c-102">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4a36c-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="4a36c-103">提供方法，可讓主應用程式明確要求的 common language runtime (CLR) 建立新的工作、 取得目前執行的工作，以及設定地理語言和文化特性的工作。</span><span class="sxs-lookup"><span data-stu-id="4a36c-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a36c-104">方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-104">Methods</span></span>  
  
|<span data-ttu-id="4a36c-105">方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-105">Method</span></span>|<span data-ttu-id="4a36c-106">描述</span><span class="sxs-lookup"><span data-stu-id="4a36c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a36c-107">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-107">CreateTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|<span data-ttu-id="4a36c-108">明確要求 CLR 建立的新[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a36c-108">Requests explicitly that the CLR create a new [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="4a36c-109">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-109">GetCurrentTask Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="4a36c-110">取得`ICLRTask`代表目前正在執行工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a36c-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="4a36c-111">GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-111">GetCurrentTaskType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="4a36c-112">取得目前執行之工作的類型。</span><span class="sxs-lookup"><span data-stu-id="4a36c-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="4a36c-113">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-113">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="4a36c-114">通知主機已修改目前執行之工作的地區設定識別項的 CLR。</span><span class="sxs-lookup"><span data-stu-id="4a36c-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="4a36c-115">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="4a36c-115">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="4a36c-116">通知 common language runtime 主應用程式已修改目前執行的工作中的使用者介面的地區設定識別項。</span><span class="sxs-lookup"><span data-stu-id="4a36c-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a36c-117">備註</span><span class="sxs-lookup"><span data-stu-id="4a36c-117">Remarks</span></span>  
 <span data-ttu-id="4a36c-118">裝載環境中執行每項工作有表示這兩種在主機端建立 (執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) 和 CLR 端 (的執行個體[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md))。</span><span class="sxs-lookup"><span data-stu-id="4a36c-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)).</span></span> <span data-ttu-id="4a36c-119">主機或 CLR 就會起始工作，建立，但必須與以確保成功通訊，在主機與工作相關 CLR 之間對應的 CLR 端表示相關聯的主應用程式端表示。</span><span class="sxs-lookup"><span data-stu-id="4a36c-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="4a36c-120">必須建立和具現化 managed 程式碼可以在作業系統執行緒上執行之前的兩個物件。</span><span class="sxs-lookup"><span data-stu-id="4a36c-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a36c-121">需求</span><span class="sxs-lookup"><span data-stu-id="4a36c-121">Requirements</span></span>  
 <span data-ttu-id="4a36c-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a36c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a36c-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a36c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a36c-124">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4a36c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a36c-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a36c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a36c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a36c-126">See Also</span></span>  
 [<span data-ttu-id="4a36c-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="4a36c-127">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="4a36c-128">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="4a36c-128">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="4a36c-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="4a36c-129">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="4a36c-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4a36c-130">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

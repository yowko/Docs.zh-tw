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
ms.openlocfilehash: 1170b29c01275b108a6ccdf6e324c96d97c10c82
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732446"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="72a6f-102">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="72a6f-102">ICLRTaskManager Interface</span></span>

<span data-ttu-id="72a6f-103">提供的方法可讓主機明確要求 common language runtime (CLR) 建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。</span><span class="sxs-lookup"><span data-stu-id="72a6f-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72a6f-104">方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-104">Methods</span></span>  
  
|<span data-ttu-id="72a6f-105">方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-105">Method</span></span>|<span data-ttu-id="72a6f-106">描述</span><span class="sxs-lookup"><span data-stu-id="72a6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72a6f-107">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-107">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="72a6f-108">明確要求 CLR 建立新的 [ICLRTask](iclrtask-interface.md) 實例。</span><span class="sxs-lookup"><span data-stu-id="72a6f-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="72a6f-109">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="72a6f-110">取得 `ICLRTask` 表示目前正在執行之工作的實例。</span><span class="sxs-lookup"><span data-stu-id="72a6f-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="72a6f-111">GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="72a6f-112">取得目前正在執行之工作的類型。</span><span class="sxs-lookup"><span data-stu-id="72a6f-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="72a6f-113">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="72a6f-114">通知 CLR，主機已修改目前正在執行之工作的地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="72a6f-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="72a6f-115">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="72a6f-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="72a6f-116">通知 common language runtime，主機已修改目前正在執行之工作的使用者介面地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="72a6f-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a6f-117">備註</span><span class="sxs-lookup"><span data-stu-id="72a6f-117">Remarks</span></span>  

 <span data-ttu-id="72a6f-118">在裝載環境中執行的每個工作，在主控制項端都具有表示 [IHostTask](ihosttask-interface.md) 實例的 () 和 CLR 端 [ () 的](iclrtask-interface.md) 實例。</span><span class="sxs-lookup"><span data-stu-id="72a6f-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="72a6f-119">主機或 CLR 可以起始工作的建立，但主機端標記法必須與對應的 CLR 端表示相關聯，以確保主控制項和 CLR 之間的通訊成功與工作相關。</span><span class="sxs-lookup"><span data-stu-id="72a6f-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="72a6f-120">這兩個物件必須先建立並具現化，managed 程式碼才能在作業系統執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="72a6f-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a6f-121">需求</span><span class="sxs-lookup"><span data-stu-id="72a6f-121">Requirements</span></span>  

 <span data-ttu-id="72a6f-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72a6f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a6f-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="72a6f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72a6f-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="72a6f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72a6f-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a6f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a6f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72a6f-126">See also</span></span>

- [<span data-ttu-id="72a6f-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="72a6f-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="72a6f-128">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="72a6f-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="72a6f-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="72a6f-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="72a6f-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="72a6f-130">Hosting Interfaces</span></span>](hosting-interfaces.md)

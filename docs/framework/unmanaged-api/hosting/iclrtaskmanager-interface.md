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
ms.openlocfilehash: f918d4e7b95922734d70ed832581e6c494c70b05
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501634"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="b55ae-102">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b55ae-102">ICLRTaskManager Interface</span></span>
<span data-ttu-id="b55ae-103">提供的方法可讓主機明確要求 common language runtime （CLR）建立新的工作、取得目前正在執行的工作，以及設定工作的地理語言和文化特性。</span><span class="sxs-lookup"><span data-stu-id="b55ae-103">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b55ae-104">方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-104">Methods</span></span>  
  
|<span data-ttu-id="b55ae-105">方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-105">Method</span></span>|<span data-ttu-id="b55ae-106">描述</span><span class="sxs-lookup"><span data-stu-id="b55ae-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b55ae-107">CreateTask 方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-107">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="b55ae-108">明確要求 CLR 建立新的[ICLRTask](iclrtask-interface.md)實例。</span><span class="sxs-lookup"><span data-stu-id="b55ae-108">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="b55ae-109">GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-109">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="b55ae-110">取得 `ICLRTask` 表示目前正在執行之工作的實例。</span><span class="sxs-lookup"><span data-stu-id="b55ae-110">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="b55ae-111">GetCurrentTaskType 方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-111">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="b55ae-112">取得目前正在執行之工作的型別。</span><span class="sxs-lookup"><span data-stu-id="b55ae-112">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="b55ae-113">SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-113">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="b55ae-114">通知 CLR，主機已修改目前正在執行之工作的地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="b55ae-114">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="b55ae-115">SetUILocale 方法</span><span class="sxs-lookup"><span data-stu-id="b55ae-115">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="b55ae-116">通知 common language runtime，主機已修改目前正在執行之工作的使用者介面地區設定識別碼。</span><span class="sxs-lookup"><span data-stu-id="b55ae-116">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b55ae-117">備註</span><span class="sxs-lookup"><span data-stu-id="b55ae-117">Remarks</span></span>  
 <span data-ttu-id="b55ae-118">在主控環境中執行的每個工作都有主機端（ [IHostTask](ihosttask-interface.md)的實例）和 CLR 端（ [ICLRTask](iclrtask-interface.md)的實例）的標記法。</span><span class="sxs-lookup"><span data-stu-id="b55ae-118">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="b55ae-119">主機或 CLR 可以起始工作的建立作業，但主機端標記法必須與對應的 CLR 端表示相關聯，以確保主機與 CLR 之間的工作相關成功通訊。</span><span class="sxs-lookup"><span data-stu-id="b55ae-119">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="b55ae-120">您必須先建立和具現化這兩個物件，然後才能在作業系統執行緒上執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b55ae-120">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b55ae-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="b55ae-121">Requirements</span></span>  
 <span data-ttu-id="b55ae-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b55ae-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b55ae-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b55ae-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b55ae-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b55ae-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b55ae-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b55ae-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b55ae-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b55ae-126">See also</span></span>

- [<span data-ttu-id="b55ae-127">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b55ae-127">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b55ae-128">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b55ae-128">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b55ae-129">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b55ae-129">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="b55ae-130">裝載介面</span><span class="sxs-lookup"><span data-stu-id="b55ae-130">Hosting Interfaces</span></span>](hosting-interfaces.md)

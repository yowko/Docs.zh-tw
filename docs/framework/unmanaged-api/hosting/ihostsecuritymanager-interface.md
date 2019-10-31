---
title: IHostSecurityManager 介面
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121484"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="c5c1c-102">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="c5c1c-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="c5c1c-103">提供的方法可讓您存取和控制目前執行之執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5c1c-104">方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-104">Methods</span></span>  
  
|<span data-ttu-id="c5c1c-105">方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-105">Method</span></span>|<span data-ttu-id="c5c1c-106">描述</span><span class="sxs-lookup"><span data-stu-id="c5c1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5c1c-107">GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="c5c1c-108">從主機取得要求的[IHostSecurityCoNtext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="c5c1c-109">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="c5c1c-110">要求使用目前使用者識別的認證來執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="c5c1c-111">OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="c5c1c-112">開啟與目前線程相關聯的任意存取權杖。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="c5c1c-113">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="c5c1c-114">終止目前使用者身分識別的模擬，並傳回原始的執行緒 token。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="c5c1c-115">SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="c5c1c-116">設定目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="c5c1c-117">SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1c-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="c5c1c-118">設定目前執行中線程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5c1c-119">備註</span><span class="sxs-lookup"><span data-stu-id="c5c1c-119">Remarks</span></span>  
 <span data-ttu-id="c5c1c-120">主機可以透過 common language runtime （CLR）和使用者程式碼，控制執行緒標記的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="c5c1c-121">它也可以確保以限制的程式碼存取，在非同步作業或程式碼點之間傳遞完整的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="c5c1c-122">`IHostSecurityContext` 封裝此安全性內容資訊，這對 CLR 而言是不透明的。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="c5c1c-123">CLR 會在內部處理 managed 執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="c5c1c-124">在下列情況下，它會查詢進程特定的 `IHostSecurityManager`：</span><span class="sxs-lookup"><span data-stu-id="c5c1c-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="c5c1c-125">在完成項執行緒中，于完成項執行期間。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="c5c1c-126">在類別和模組的函式執行期間。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="c5c1c-127">在背景工作執行緒上的非同步點上，呼叫[IHostThreadPoolManager：： QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="c5c1c-128">I/o 完成通訊埠的服務。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c1c-129">需求</span><span class="sxs-lookup"><span data-stu-id="c5c1c-129">Requirements</span></span>  
 <span data-ttu-id="c5c1c-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5c1c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c1c-131">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c5c1c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5c1c-132">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c5c1c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5c1c-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c1c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c1c-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5c1c-134">See also</span></span>

- [<span data-ttu-id="c5c1c-135">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="c5c1c-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="c5c1c-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="c5c1c-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

---
title: "IHostSecurityManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b3d67328dbf68491d319e55e63a9c3540cd1ee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="d0888-102">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="d0888-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="d0888-103">提供方法，讓存取與目前執行中執行緒的安全性內容的控制。</span><span class="sxs-lookup"><span data-stu-id="d0888-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0888-104">方法</span><span class="sxs-lookup"><span data-stu-id="d0888-104">Methods</span></span>  
  
|<span data-ttu-id="d0888-105">方法</span><span class="sxs-lookup"><span data-stu-id="d0888-105">Method</span></span>|<span data-ttu-id="d0888-106">說明</span><span class="sxs-lookup"><span data-stu-id="d0888-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0888-107">GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="d0888-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="d0888-108">取得所要求[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)從主機。</span><span class="sxs-lookup"><span data-stu-id="d0888-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="d0888-109">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="d0888-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="d0888-110">要求執行程式碼會使用目前的使用者身分識別的認證。</span><span class="sxs-lookup"><span data-stu-id="d0888-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="d0888-111">OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="d0888-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="d0888-112">會開啟與目前執行緒相關聯的判別存取權杖。</span><span class="sxs-lookup"><span data-stu-id="d0888-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="d0888-113">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="d0888-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="d0888-114">結束目前的使用者身分識別模擬並傳回原始的執行緒語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d0888-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="d0888-115">SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="d0888-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="d0888-116">設定目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="d0888-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="d0888-117">SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="d0888-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="d0888-118">設定目前執行中執行緒的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d0888-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0888-119">備註</span><span class="sxs-lookup"><span data-stu-id="d0888-119">Remarks</span></span>  
 <span data-ttu-id="d0888-120">主機可控制由 common language runtime (CLR) 和使用者程式碼的執行緒語彙基元的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="d0888-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="d0888-121">它也可以確保完整的安全性內容資訊傳遞到非同步作業或字碼指標，具有受限制的程式碼存取權。</span><span class="sxs-lookup"><span data-stu-id="d0888-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="d0888-122">`IHostSecurityContext`封裝這個資訊安全內容資訊，也就是不透明 CLR。</span><span class="sxs-lookup"><span data-stu-id="d0888-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="d0888-123">CLR 會在內部處理 managed 的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="d0888-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="d0888-124">它會查詢處理序專屬`IHostSecurityManager`在下列情況：</span><span class="sxs-lookup"><span data-stu-id="d0888-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
-   <span data-ttu-id="d0888-125">完成項執行緒上、 完成項執行期間。</span><span class="sxs-lookup"><span data-stu-id="d0888-125">On the finalizer thread, during finalizer execution.</span></span>  
  
-   <span data-ttu-id="d0888-126">在類別和模組的建構函式執行。</span><span class="sxs-lookup"><span data-stu-id="d0888-126">During class and module constructor execution.</span></span>  
  
-   <span data-ttu-id="d0888-127">在非同步背景工作執行緒，在呼叫點[ihostthreadpoolmanager:: Queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d0888-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
-   <span data-ttu-id="d0888-128">在服務的 I/O 完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="d0888-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0888-129">需求</span><span class="sxs-lookup"><span data-stu-id="d0888-129">Requirements</span></span>  
 <span data-ttu-id="d0888-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0888-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0888-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d0888-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0888-132">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d0888-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0888-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0888-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0888-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0888-134">See Also</span></span>  
 [<span data-ttu-id="d0888-135">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="d0888-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="d0888-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d0888-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2c71f32dfd190e188bb28aad5d51c72160eb4bc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603245"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="962b5-102">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="962b5-102">IHostSecurityManager Interface</span></span>
<span data-ttu-id="962b5-103">提供方法，讓存取權和控制權的目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="962b5-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="962b5-104">方法</span><span class="sxs-lookup"><span data-stu-id="962b5-104">Methods</span></span>  
  
|<span data-ttu-id="962b5-105">方法</span><span class="sxs-lookup"><span data-stu-id="962b5-105">Method</span></span>|<span data-ttu-id="962b5-106">描述</span><span class="sxs-lookup"><span data-stu-id="962b5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="962b5-107">GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="962b5-107">GetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="962b5-108">取得要求[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)從主應用程式。</span><span class="sxs-lookup"><span data-stu-id="962b5-108">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="962b5-109">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="962b5-109">ImpersonateLoggedOnUser Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="962b5-110">要求執行程式碼會使用目前的使用者身分識別的認證。</span><span class="sxs-lookup"><span data-stu-id="962b5-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="962b5-111">OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="962b5-111">OpenThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="962b5-112">開啟與目前執行緒相關聯的 discretionary 存取權杖。</span><span class="sxs-lookup"><span data-stu-id="962b5-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="962b5-113">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="962b5-113">RevertToSelf Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="962b5-114">終止目前的使用者身分識別模擬，並傳回原始的執行緒 token。</span><span class="sxs-lookup"><span data-stu-id="962b5-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="962b5-115">SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="962b5-115">SetSecurityContext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="962b5-116">設定目前執行中執行緒的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="962b5-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="962b5-117">SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="962b5-117">SetThreadToken Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="962b5-118">設定目前執行中執行緒的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="962b5-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="962b5-119">備註</span><span class="sxs-lookup"><span data-stu-id="962b5-119">Remarks</span></span>  
 <span data-ttu-id="962b5-120">主機可以控制執行緒權杖的所有程式碼存取的通用語言執行平台 (CLR) 」 和 「 使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="962b5-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="962b5-121">它也可以確保完整的安全性內容資訊傳遞到非同步作業或受限制的程式碼存取的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="962b5-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="962b5-122">`IHostSecurityContext` 封裝此資訊安全內容資訊，也就是對 CLR 不透明。</span><span class="sxs-lookup"><span data-stu-id="962b5-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="962b5-123">CLR 會在內部處理 managed 的執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="962b5-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="962b5-124">它會查詢處理序專屬`IHostSecurityManager`在下列情況：</span><span class="sxs-lookup"><span data-stu-id="962b5-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="962b5-125">在完成項執行期間的完成項執行緒。</span><span class="sxs-lookup"><span data-stu-id="962b5-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="962b5-126">在類別和模組的建構函式執行。</span><span class="sxs-lookup"><span data-stu-id="962b5-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="962b5-127">在背景工作執行緒的呼叫中的非同步點[ihostthreadpoolmanager:: Queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="962b5-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="962b5-128">在服務的 I/O 完成連接埠。</span><span class="sxs-lookup"><span data-stu-id="962b5-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962b5-129">需求</span><span class="sxs-lookup"><span data-stu-id="962b5-129">Requirements</span></span>  
 <span data-ttu-id="962b5-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="962b5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="962b5-131">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="962b5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="962b5-132">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="962b5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="962b5-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="962b5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962b5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="962b5-134">See also</span></span>

- [<span data-ttu-id="962b5-135">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="962b5-135">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="962b5-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="962b5-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

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
ms.openlocfilehash: 37f606a67bef79936c81b2a36f12a00d24bd82f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680530"
---
# <a name="ihostsecuritymanager-interface"></a><span data-ttu-id="4660e-102">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="4660e-102">IHostSecurityManager Interface</span></span>

<span data-ttu-id="4660e-103">提供方法，可讓您存取和控制目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="4660e-103">Provides methods that allow access to and control over the security context of the currently executing thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4660e-104">方法</span><span class="sxs-lookup"><span data-stu-id="4660e-104">Methods</span></span>  
  
|<span data-ttu-id="4660e-105">方法</span><span class="sxs-lookup"><span data-stu-id="4660e-105">Method</span></span>|<span data-ttu-id="4660e-106">描述</span><span class="sxs-lookup"><span data-stu-id="4660e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4660e-107">GetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="4660e-107">GetSecurityContext Method</span></span>](ihostsecuritymanager-getsecuritycontext-method.md)|<span data-ttu-id="4660e-108">從主機取得要求的 [IHostSecurityCoNtext](ihostsecuritycontext-interface.md) 。</span><span class="sxs-lookup"><span data-stu-id="4660e-108">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>|  
|[<span data-ttu-id="4660e-109">ImpersonateLoggedOnUser 方法</span><span class="sxs-lookup"><span data-stu-id="4660e-109">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)|<span data-ttu-id="4660e-110">要求使用目前使用者身分識別的認證來執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="4660e-110">Requests that code be executed using the credentials of the current user identity.</span></span>|  
|[<span data-ttu-id="4660e-111">OpenThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="4660e-111">OpenThreadToken Method</span></span>](ihostsecuritymanager-openthreadtoken-method.md)|<span data-ttu-id="4660e-112">開啟與目前線程相關聯的任意存取權杖。</span><span class="sxs-lookup"><span data-stu-id="4660e-112">Opens the discretionary access token associated with the current thread.</span></span>|  
|[<span data-ttu-id="4660e-113">RevertToSelf 方法</span><span class="sxs-lookup"><span data-stu-id="4660e-113">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)|<span data-ttu-id="4660e-114">終止目前使用者身分識別的模擬，並傳回原始執行緒 token。</span><span class="sxs-lookup"><span data-stu-id="4660e-114">Terminates impersonation of the current user identity and returns the original thread token.</span></span>|  
|[<span data-ttu-id="4660e-115">SetSecurityContext 方法</span><span class="sxs-lookup"><span data-stu-id="4660e-115">SetSecurityContext Method</span></span>](ihostsecuritymanager-setsecuritycontext-method.md)|<span data-ttu-id="4660e-116">設定目前執行中線程的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="4660e-116">Sets the security context for the currently executing thread.</span></span>|  
|[<span data-ttu-id="4660e-117">SetThreadToken 方法</span><span class="sxs-lookup"><span data-stu-id="4660e-117">SetThreadToken Method</span></span>](ihostsecuritymanager-setthreadtoken-method.md)|<span data-ttu-id="4660e-118">設定目前執行中線程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="4660e-118">Sets a handle for the currently executing thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4660e-119">備註</span><span class="sxs-lookup"><span data-stu-id="4660e-119">Remarks</span></span>  

 <span data-ttu-id="4660e-120">主機可以透過 common language runtime (CLR) 和使用者程式碼，控制執行緒權杖的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="4660e-120">A host can control all code access to thread tokens by both the common language runtime (CLR) and user code.</span></span> <span data-ttu-id="4660e-121">它也可以確保在非同步作業或具有限制程式碼存取的程式碼點之間傳遞完整的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="4660e-121">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="4660e-122">`IHostSecurityContext` 封裝此安全性內容資訊，這對 CLR 而言是不透明的。</span><span class="sxs-lookup"><span data-stu-id="4660e-122">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span>  
  
 <span data-ttu-id="4660e-123">CLR 會在內部處理 managed 執行緒內容。</span><span class="sxs-lookup"><span data-stu-id="4660e-123">The CLR handles managed thread context internally.</span></span> <span data-ttu-id="4660e-124">它會 `IHostSecurityManager` 在下列情況下查詢特定進程：</span><span class="sxs-lookup"><span data-stu-id="4660e-124">It queries the process-specific `IHostSecurityManager` in the following situations:</span></span>  
  
- <span data-ttu-id="4660e-125">在完成項執行緒上，于完成項執行期間。</span><span class="sxs-lookup"><span data-stu-id="4660e-125">On the finalizer thread, during finalizer execution.</span></span>  
  
- <span data-ttu-id="4660e-126">在類別和模組的函式執行期間。</span><span class="sxs-lookup"><span data-stu-id="4660e-126">During class and module constructor execution.</span></span>  
  
- <span data-ttu-id="4660e-127">在背景工作執行緒上的非同步點上，呼叫 [IHostThreadPoolManager：： QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="4660e-127">At asynchronous points on the worker thread, in calls to the [IHostThreadPoolManager::QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) method.</span></span>  
  
- <span data-ttu-id="4660e-128">提供 i/o 完成埠的服務。</span><span class="sxs-lookup"><span data-stu-id="4660e-128">In servicing of I/O completion ports.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4660e-129">需求</span><span class="sxs-lookup"><span data-stu-id="4660e-129">Requirements</span></span>  

 <span data-ttu-id="4660e-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4660e-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4660e-131">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4660e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4660e-132">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="4660e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4660e-133">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4660e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4660e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4660e-134">See also</span></span>

- [<span data-ttu-id="4660e-135">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="4660e-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="4660e-136">裝載介面</span><span class="sxs-lookup"><span data-stu-id="4660e-136">Hosting Interfaces</span></span>](hosting-interfaces.md)

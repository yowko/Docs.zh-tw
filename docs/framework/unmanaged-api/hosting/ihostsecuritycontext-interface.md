---
title: IHostSecurityContext 介面
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984291"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="df78b-102">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="df78b-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="df78b-103">可讓 common language runtime (CLR) 會維護由主機實作的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="df78b-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df78b-104">方法</span><span class="sxs-lookup"><span data-stu-id="df78b-104">Methods</span></span>  
  
|<span data-ttu-id="df78b-105">方法</span><span class="sxs-lookup"><span data-stu-id="df78b-105">Method</span></span>|<span data-ttu-id="df78b-106">描述</span><span class="sxs-lookup"><span data-stu-id="df78b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df78b-107">Capture 方法</span><span class="sxs-lookup"><span data-stu-id="df78b-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="df78b-108">取得的複製品`IHostSecurityContext`呼叫傳回的執行個體[ihostsecuritymanager:: Getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)。</span><span class="sxs-lookup"><span data-stu-id="df78b-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df78b-109">備註</span><span class="sxs-lookup"><span data-stu-id="df78b-109">Remarks</span></span>  
 <span data-ttu-id="df78b-110">主機可以控制執行緒權杖的所有程式碼存取 CLR 和使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="df78b-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="df78b-111">它也可以確保完整的安全性內容資訊傳遞到非同步作業或受限制的程式碼存取的字碼指標。</span><span class="sxs-lookup"><span data-stu-id="df78b-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="df78b-112">`IHostSecurityContext` 封裝此安全性內容資訊，對執行階段是不透明。</span><span class="sxs-lookup"><span data-stu-id="df78b-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="df78b-113">此資訊使用的執行階段擷取`Capture`，並將它移動跨執行緒集區背景工作項目分派、 完成項執行和模組和類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="df78b-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df78b-114">需求</span><span class="sxs-lookup"><span data-stu-id="df78b-114">Requirements</span></span>  
 <span data-ttu-id="df78b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df78b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df78b-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df78b-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df78b-117">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="df78b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df78b-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df78b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df78b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df78b-119">See also</span></span>

- [<span data-ttu-id="df78b-120">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="df78b-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="df78b-121">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="df78b-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="df78b-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="df78b-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

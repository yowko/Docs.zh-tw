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
ms.openlocfilehash: aafaa1d648396ddaa76193fa15cf7f74394777a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724802"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="0773f-102">IHostSecurityContext 介面</span><span class="sxs-lookup"><span data-stu-id="0773f-102">IHostSecurityContext Interface</span></span>

<span data-ttu-id="0773f-103">允許 common language runtime (CLR) 維護主機所執行的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="0773f-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0773f-104">方法</span><span class="sxs-lookup"><span data-stu-id="0773f-104">Methods</span></span>  
  
|<span data-ttu-id="0773f-105">方法</span><span class="sxs-lookup"><span data-stu-id="0773f-105">Method</span></span>|<span data-ttu-id="0773f-106">描述</span><span class="sxs-lookup"><span data-stu-id="0773f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0773f-107">Capture 方法</span><span class="sxs-lookup"><span data-stu-id="0773f-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="0773f-108">取得 `IHostSecurityContext` 從呼叫 [IHostSecurityManager：： GetSecurityCoNtext](ihostsecuritymanager-getsecuritycontext-method.md)所傳回之實例的複本。</span><span class="sxs-lookup"><span data-stu-id="0773f-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0773f-109">備註</span><span class="sxs-lookup"><span data-stu-id="0773f-109">Remarks</span></span>  

 <span data-ttu-id="0773f-110">主機可以透過 CLR 和使用者程式碼控制執行緒權杖的所有程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0773f-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="0773f-111">它也可以確保在非同步作業或具有限制程式碼存取的程式碼點之間傳遞完整的安全性內容資訊。</span><span class="sxs-lookup"><span data-stu-id="0773f-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="0773f-112">`IHostSecurityContext` 封裝此安全性內容資訊，這對執行時間而言是不透明的。</span><span class="sxs-lookup"><span data-stu-id="0773f-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="0773f-113">執行時間會使用來捕捉此資訊 `Capture` ，並將其移動到執行緒集區背景工作專案分派、完成項執行，以及模組和類別的函式。</span><span class="sxs-lookup"><span data-stu-id="0773f-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0773f-114">需求</span><span class="sxs-lookup"><span data-stu-id="0773f-114">Requirements</span></span>  

 <span data-ttu-id="0773f-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0773f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0773f-116">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0773f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0773f-117">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0773f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0773f-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0773f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0773f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0773f-119">See also</span></span>

- [<span data-ttu-id="0773f-120">ICLRHostProtectionManager 介面</span><span class="sxs-lookup"><span data-stu-id="0773f-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="0773f-121">IHostSecurityManager 介面</span><span class="sxs-lookup"><span data-stu-id="0773f-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="0773f-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="0773f-122">Hosting Interfaces</span></span>](hosting-interfaces.md)

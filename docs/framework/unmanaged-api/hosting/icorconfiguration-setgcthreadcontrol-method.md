---
title: "ICorConfiguration::SetGCThreadControl 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b6b28b67f924df4d7f587d0364bce2a853f60b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="7d99e-102">ICorConfiguration::SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="7d99e-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="7d99e-103">設定排程執行緒非執行階段工作，否則會封鎖記憶體回收的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="7d99e-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d99e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d99e-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d99e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7d99e-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="7d99e-106">[in]指標[IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)通知主機有關的暫止的執行緒非執行階段工作的物件。</span><span class="sxs-lookup"><span data-stu-id="7d99e-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d99e-107">備註</span><span class="sxs-lookup"><span data-stu-id="7d99e-107">Remarks</span></span>  
 <span data-ttu-id="7d99e-108">主機可以選擇在[igcthreadcontrol:: Threadisblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)回呼是否要重新排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="7d99e-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d99e-109">需求</span><span class="sxs-lookup"><span data-stu-id="7d99e-109">Requirements</span></span>  
 <span data-ttu-id="7d99e-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d99e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d99e-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d99e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d99e-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7d99e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d99e-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d99e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d99e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7d99e-114">See Also</span></span>  
 [<span data-ttu-id="7d99e-115">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="7d99e-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)

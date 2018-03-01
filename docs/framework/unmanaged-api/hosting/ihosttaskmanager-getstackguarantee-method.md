---
title: "IHostTaskManager::GetStackGuarantee 方法"
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
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a2e4829083715fad8d77c1b5a2c303a07d5684ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="6d573-102">IHostTaskManager::GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="6d573-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="6d573-103">取得量保證堆疊操作完成之後, 可供使用的堆疊空間但之前結束處理序。</span><span class="sxs-lookup"><span data-stu-id="6d573-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d573-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d573-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d573-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d573-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="6d573-106">[out]可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="6d573-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d573-107">需求</span><span class="sxs-lookup"><span data-stu-id="6d573-107">Requirements</span></span>  
 <span data-ttu-id="6d573-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d573-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d573-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d573-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d573-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6d573-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d573-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d573-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d573-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6d573-112">See Also</span></span>  
 [<span data-ttu-id="6d573-113">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6d573-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

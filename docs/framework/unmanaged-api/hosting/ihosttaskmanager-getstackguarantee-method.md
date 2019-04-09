---
title: IHostTaskManager::GetStackGuarantee 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea1c1f998febccbc80fb10cef5a8dfd229e1987e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095941"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="9e556-102">IHostTaskManager::GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="9e556-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="9e556-103">取得量的保證堆疊操作完成之後, 才能使用的堆疊空間，但處理程序關閉之前。</span><span class="sxs-lookup"><span data-stu-id="9e556-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e556-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e556-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e556-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e556-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="9e556-106">[out]可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="9e556-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e556-107">需求</span><span class="sxs-lookup"><span data-stu-id="9e556-107">Requirements</span></span>  
 <span data-ttu-id="9e556-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e556-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e556-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e556-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e556-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e556-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9e556-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="9e556-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e556-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e556-112">See also</span></span>

- [<span data-ttu-id="9e556-113">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="9e556-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

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
ms.openlocfilehash: 739670fb84eb0145fd8bf8073f453518487c38b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749580"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="caeec-102">IHostTaskManager::GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="caeec-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="caeec-103">取得量的保證堆疊操作完成之後, 才能使用的堆疊空間，但處理程序關閉之前。</span><span class="sxs-lookup"><span data-stu-id="caeec-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caeec-104">語法</span><span class="sxs-lookup"><span data-stu-id="caeec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caeec-105">參數</span><span class="sxs-lookup"><span data-stu-id="caeec-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="caeec-106">[out]可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="caeec-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caeec-107">需求</span><span class="sxs-lookup"><span data-stu-id="caeec-107">Requirements</span></span>  
 <span data-ttu-id="caeec-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="caeec-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caeec-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="caeec-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="caeec-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="caeec-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="caeec-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caeec-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caeec-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caeec-112">See also</span></span>

- [<span data-ttu-id="caeec-113">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="caeec-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

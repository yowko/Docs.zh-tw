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
ms.openlocfilehash: 22ec34c82d0f8e550dfc8941f2c048ebed6cf1d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133029"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="7ef4a-102">IHostTaskManager::GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="7ef4a-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="7ef4a-103">取得堆疊作業完成後，但在關閉進程之前，保證可以使用的堆疊空間量。</span><span class="sxs-lookup"><span data-stu-id="7ef4a-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ef4a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ef4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ef4a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ef4a-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="7ef4a-106">脫銷可用位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="7ef4a-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ef4a-107">需求</span><span class="sxs-lookup"><span data-stu-id="7ef4a-107">Requirements</span></span>  
 <span data-ttu-id="7ef4a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ef4a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ef4a-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="7ef4a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ef4a-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7ef4a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ef4a-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ef4a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ef4a-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ef4a-112">See also</span></span>

- [<span data-ttu-id="7ef4a-113">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="7ef4a-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

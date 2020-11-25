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
ms.openlocfilehash: 718e6f3f19a5c368091c8a8aad3bd1f6598228df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727272"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="e2c6f-102">IHostTaskManager::GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="e2c6f-102">IHostTaskManager::GetStackGuarantee Method</span></span>

<span data-ttu-id="e2c6f-103">取得在堆疊作業完成之後，但在進程關閉之前，保證可供使用的堆疊空間量。</span><span class="sxs-lookup"><span data-stu-id="e2c6f-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2c6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2c6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2c6f-105">Parameters</span></span>  

 `pGuarantee`  
 <span data-ttu-id="e2c6f-106">擴展可用位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="e2c6f-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2c6f-107">需求</span><span class="sxs-lookup"><span data-stu-id="e2c6f-107">Requirements</span></span>  

 <span data-ttu-id="e2c6f-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c6f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2c6f-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e2c6f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2c6f-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e2c6f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2c6f-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c6f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c6f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2c6f-112">See also</span></span>

- [<span data-ttu-id="e2c6f-113">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="e2c6f-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

---
title: "IHostTaskManager::GetStackGuarantee 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetStackGuarantee
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 691eaa2bd462af5fff0b222e991c13032ddb1af1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="6b9b6-102">IHostTaskManager::GetStackGuarantee 方法</span><span class="sxs-lookup"><span data-stu-id="6b9b6-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="6b9b6-103">取得量保證堆疊操作完成之後, 可供使用的堆疊空間但之前結束處理序。</span><span class="sxs-lookup"><span data-stu-id="6b9b6-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b9b6-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b9b6-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b9b6-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="6b9b6-106">[out]可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="6b9b6-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b9b6-107">需求</span><span class="sxs-lookup"><span data-stu-id="6b9b6-107">Requirements</span></span>  
 <span data-ttu-id="6b9b6-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b9b6-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b9b6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b9b6-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6b9b6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b9b6-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b9b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9b6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b9b6-112">See Also</span></span>  
 [<span data-ttu-id="6b9b6-113">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="6b9b6-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

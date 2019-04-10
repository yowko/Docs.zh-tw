---
title: ICorThreadpool::CorGetAvailableThreads 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c929b9434507ea7cce936767f2ac72ff98fda7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215790"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="0bd2f-102">ICorThreadpool::CorGetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0bd2f-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="0bd2f-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="0bd2f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd2f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bd2f-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0bd2f-105">需求</span><span class="sxs-lookup"><span data-stu-id="0bd2f-105">Requirements</span></span>  
 <span data-ttu-id="0bd2f-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bd2f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd2f-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0bd2f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0bd2f-108">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0bd2f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0bd2f-109">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0bd2f-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0bd2f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bd2f-110">See also</span></span>

- [<span data-ttu-id="0bd2f-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="0bd2f-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

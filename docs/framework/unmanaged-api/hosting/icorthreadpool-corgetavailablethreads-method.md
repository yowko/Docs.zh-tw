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
ms.openlocfilehash: 20b600eb50ca4992e20b991406d18a91feae5c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574448"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="2d4bd-102">ICorThreadpool::CorGetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="2d4bd-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="2d4bd-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="2d4bd-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d4bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d4bd-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2d4bd-105">需求</span><span class="sxs-lookup"><span data-stu-id="2d4bd-105">Requirements</span></span>  
 <span data-ttu-id="2d4bd-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d4bd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d4bd-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d4bd-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d4bd-108">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2d4bd-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d4bd-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d4bd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4bd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d4bd-110">See also</span></span>
- [<span data-ttu-id="2d4bd-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="2d4bd-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

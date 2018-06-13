---
title: ICorThreadpool::CorGetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c25f39cf64f462ac319803354e6a2a54ea482b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436932"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="2c1dd-102">ICorThreadpool::CorGetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="2c1dd-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="2c1dd-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="2c1dd-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c1dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c1dd-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2c1dd-105">需求</span><span class="sxs-lookup"><span data-stu-id="2c1dd-105">Requirements</span></span>  
 <span data-ttu-id="2c1dd-106">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c1dd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c1dd-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2c1dd-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c1dd-108">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2c1dd-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c1dd-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c1dd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1dd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c1dd-110">See Also</span></span>  
 [<span data-ttu-id="2c1dd-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="2c1dd-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

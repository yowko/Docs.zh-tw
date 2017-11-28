---
title: "ICorThreadpool::CorSetMaxThreads 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorSetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 384b214ac38eb99ce45bf3050f33f35702813c69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="5d5fa-102">ICorThreadpool::CorSetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="5d5fa-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="5d5fa-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="5d5fa-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d5fa-104">Syntax</span></span>  
  
```  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5d5fa-105">需求</span><span class="sxs-lookup"><span data-stu-id="5d5fa-105">Requirements</span></span>  
 <span data-ttu-id="5d5fa-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d5fa-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d5fa-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d5fa-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d5fa-108">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5d5fa-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d5fa-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d5fa-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5fa-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d5fa-110">See Also</span></span>  
 [<span data-ttu-id="5d5fa-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="5d5fa-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

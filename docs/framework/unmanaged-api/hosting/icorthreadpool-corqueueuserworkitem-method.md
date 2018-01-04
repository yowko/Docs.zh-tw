---
title: "ICorThreadpool::CorQueueUserWorkItem 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorQueueUserWorkItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38709dc5b54ebaca59009eaf2c357ac122b6816a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="e770a-102">ICorThreadpool::CorQueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="e770a-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="e770a-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="e770a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e770a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e770a-104">Syntax</span></span>  
  
```  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e770a-105">需求</span><span class="sxs-lookup"><span data-stu-id="e770a-105">Requirements</span></span>  
 <span data-ttu-id="e770a-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e770a-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e770a-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e770a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e770a-108">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e770a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e770a-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e770a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e770a-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="e770a-110">See Also</span></span>  
 [<span data-ttu-id="e770a-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="e770a-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

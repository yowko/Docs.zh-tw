---
title: ICorThreadpool::CorBindIoCompletionCallback 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 893ec89be83cf68e9b87d4a57bc221feac9932cc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770836"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="dfcf1-102">ICorThreadpool::CorBindIoCompletionCallback 方法</span><span class="sxs-lookup"><span data-stu-id="dfcf1-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="dfcf1-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="dfcf1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfcf1-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfcf1-104">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="dfcf1-105">需求</span><span class="sxs-lookup"><span data-stu-id="dfcf1-105">Requirements</span></span>  
 <span data-ttu-id="dfcf1-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dfcf1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfcf1-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfcf1-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfcf1-108">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dfcf1-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfcf1-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfcf1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfcf1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfcf1-110">See also</span></span>

- [<span data-ttu-id="dfcf1-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="dfcf1-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

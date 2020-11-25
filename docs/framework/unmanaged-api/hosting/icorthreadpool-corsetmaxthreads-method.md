---
title: ICorThreadpool::CorSetMaxThreads 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
ms.openlocfilehash: f7d9d3d059abcf58fe0f4b35ce41046efb9c2400
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733978"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="6ab8d-102">ICorThreadpool::CorSetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="6ab8d-102">ICorThreadpool::CorSetMaxThreads Method</span></span>

<span data-ttu-id="6ab8d-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="6ab8d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab8d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ab8d-104">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6ab8d-105">需求</span><span class="sxs-lookup"><span data-stu-id="6ab8d-105">Requirements</span></span>  

 <span data-ttu-id="6ab8d-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ab8d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ab8d-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6ab8d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ab8d-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6ab8d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ab8d-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ab8d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab8d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ab8d-110">See also</span></span>

- [<span data-ttu-id="6ab8d-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="6ab8d-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

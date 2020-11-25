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
ms.openlocfilehash: 09b1f56600c05bf8e6028328adb80083b03ccc13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725768"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="e58c9-102">ICorThreadpool::CorGetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="e58c9-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>

<span data-ttu-id="e58c9-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="e58c9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58c9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e58c9-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e58c9-105">需求</span><span class="sxs-lookup"><span data-stu-id="e58c9-105">Requirements</span></span>  

 <span data-ttu-id="e58c9-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e58c9-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e58c9-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e58c9-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e58c9-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e58c9-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e58c9-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e58c9-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58c9-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e58c9-110">See also</span></span>

- [<span data-ttu-id="e58c9-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="e58c9-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

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
ms.openlocfilehash: 46ffdb21c1f3b501cc28afffc224349887af5644
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762743"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="c84f1-102">ICorThreadpool::CorGetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="c84f1-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="c84f1-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="c84f1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c84f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c84f1-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c84f1-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="c84f1-105">Requirements</span></span>  
 <span data-ttu-id="c84f1-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c84f1-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c84f1-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c84f1-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c84f1-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c84f1-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c84f1-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c84f1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84f1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c84f1-110">See also</span></span>

- [<span data-ttu-id="c84f1-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="c84f1-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

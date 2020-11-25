---
title: ICorThreadpool::CorUnregisterWait 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 38b3655da75750ffc3ea1c7983ce3b549d76f087
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733967"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="f983c-102">ICorThreadpool::CorUnregisterWait 方法</span><span class="sxs-lookup"><span data-stu-id="f983c-102">ICorThreadpool::CorUnregisterWait Method</span></span>

<span data-ttu-id="f983c-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="f983c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f983c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f983c-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f983c-105">需求</span><span class="sxs-lookup"><span data-stu-id="f983c-105">Requirements</span></span>  

 <span data-ttu-id="f983c-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f983c-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f983c-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f983c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f983c-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f983c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f983c-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f983c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f983c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f983c-110">See also</span></span>

- [<span data-ttu-id="f983c-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="f983c-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

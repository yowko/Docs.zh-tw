---
title: ICorThreadpool::CorDeleteTimer 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
ms.openlocfilehash: 97658d5418ac3c04abd423ffff86324acf0e99c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720538"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="fc1fe-102">ICorThreadpool::CorDeleteTimer 方法</span><span class="sxs-lookup"><span data-stu-id="fc1fe-102">ICorThreadpool::CorDeleteTimer Method</span></span>

<span data-ttu-id="fc1fe-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="fc1fe-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc1fe-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc1fe-104">Syntax</span></span>  
  
```cpp  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fc1fe-105">需求</span><span class="sxs-lookup"><span data-stu-id="fc1fe-105">Requirements</span></span>  

 <span data-ttu-id="fc1fe-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc1fe-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc1fe-107">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fc1fe-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc1fe-108">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="fc1fe-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc1fe-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc1fe-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1fe-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc1fe-110">See also</span></span>

- [<span data-ttu-id="fc1fe-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="fc1fe-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

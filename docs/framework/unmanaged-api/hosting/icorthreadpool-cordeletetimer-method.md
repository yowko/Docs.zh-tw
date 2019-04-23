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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 098c23dd0ddff4342aa4cefbaa4e149ed95a1cb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178343"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="5f04f-102">ICorThreadpool::CorDeleteTimer 方法</span><span class="sxs-lookup"><span data-stu-id="5f04f-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="5f04f-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="5f04f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f04f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f04f-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5f04f-105">需求</span><span class="sxs-lookup"><span data-stu-id="5f04f-105">Requirements</span></span>  
 <span data-ttu-id="5f04f-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f04f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f04f-107">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f04f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f04f-108">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5f04f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f04f-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f04f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f04f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f04f-110">See also</span></span>

- [<span data-ttu-id="5f04f-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="5f04f-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

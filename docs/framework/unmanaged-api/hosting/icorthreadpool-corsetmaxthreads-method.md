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
ms.openlocfilehash: 7f972bcfedd028d85debbbd60968a57c4d64ee0c
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760321"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="0ca93-102">ICorThreadpool::CorSetMaxThreads 方法</span><span class="sxs-lookup"><span data-stu-id="0ca93-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="0ca93-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="0ca93-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca93-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ca93-104">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0ca93-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="0ca93-105">Requirements</span></span>  
 <span data-ttu-id="0ca93-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ca93-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca93-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0ca93-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ca93-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ca93-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ca93-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca93-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca93-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca93-110">See also</span></span>

- [<span data-ttu-id="0ca93-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="0ca93-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

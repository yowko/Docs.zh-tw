---
title: ICorThreadpool::CorQueueUserWorkItem 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: 5500f2b84f00e039cbc3f669b49be467789955f0
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762730"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="74b4e-102">ICorThreadpool::CorQueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="74b4e-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="74b4e-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="74b4e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="74b4e-104">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="74b4e-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="74b4e-105">Requirements</span></span>  
 <span data-ttu-id="74b4e-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74b4e-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b4e-107">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="74b4e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74b4e-108">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="74b4e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74b4e-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b4e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b4e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74b4e-110">See also</span></span>

- [<span data-ttu-id="74b4e-111">ICorThreadpool 介面</span><span class="sxs-lookup"><span data-stu-id="74b4e-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)

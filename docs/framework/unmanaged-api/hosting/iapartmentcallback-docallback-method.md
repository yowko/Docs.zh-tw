---
title: "IApartmentCallback::DoCallback 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback.DoCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06aaab6d4ad7d33bbdc52a38c999cc925eee1666
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="989a9-102">IApartmentCallback::DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="989a9-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="989a9-103">執行指定的函式在 apartment 中。</span><span class="sxs-lookup"><span data-stu-id="989a9-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="989a9-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="989a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="989a9-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="989a9-106">[in]要在 apartment 中執行的函式指標。</span><span class="sxs-lookup"><span data-stu-id="989a9-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="989a9-107">[in]函式的引數指標。</span><span class="sxs-lookup"><span data-stu-id="989a9-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="989a9-108">需求</span><span class="sxs-lookup"><span data-stu-id="989a9-108">Requirements</span></span>  
 <span data-ttu-id="989a9-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="989a9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="989a9-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="989a9-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="989a9-111">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="989a9-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="989a9-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="989a9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989a9-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="989a9-113">See Also</span></span>  
 [<span data-ttu-id="989a9-114">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="989a9-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)

---
title: IApartmentCallback::DoCallback 方法
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77a2ccaf6f972fadd8396378dc7777ec4c85120d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110223"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="86538-102">IApartmentCallback::DoCallback 方法</span><span class="sxs-lookup"><span data-stu-id="86538-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="86538-103">執行指定的函式中的 apartment。</span><span class="sxs-lookup"><span data-stu-id="86538-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86538-104">語法</span><span class="sxs-lookup"><span data-stu-id="86538-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86538-105">參數</span><span class="sxs-lookup"><span data-stu-id="86538-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="86538-106">[in]要在 apartment 內執行的函式指標。</span><span class="sxs-lookup"><span data-stu-id="86538-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="86538-107">[in]函式的引數指標。</span><span class="sxs-lookup"><span data-stu-id="86538-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86538-108">需求</span><span class="sxs-lookup"><span data-stu-id="86538-108">Requirements</span></span>  
 <span data-ttu-id="86538-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86538-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86538-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86538-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86538-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="86538-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86538-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86538-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86538-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86538-113">See also</span></span>

- [<span data-ttu-id="86538-114">IApartmentCallback 介面</span><span class="sxs-lookup"><span data-stu-id="86538-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)

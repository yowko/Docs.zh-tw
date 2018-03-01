---
title: "IObjectHandle::Unwrap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b14483279e4416c898a836ae87c6bca180b4736
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="35766-102">IObjectHandle::Unwrap 方法</span><span class="sxs-lookup"><span data-stu-id="35766-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="35766-103">間接取值的傳值方式封送處理物件會解除包裝。</span><span class="sxs-lookup"><span data-stu-id="35766-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35766-104">語法</span><span class="sxs-lookup"><span data-stu-id="35766-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35766-105">參數</span><span class="sxs-lookup"><span data-stu-id="35766-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="35766-106">[out]要未包裝的物件指標。</span><span class="sxs-lookup"><span data-stu-id="35766-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35766-107">需求</span><span class="sxs-lookup"><span data-stu-id="35766-107">Requirements</span></span>  
 <span data-ttu-id="35766-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35766-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35766-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35766-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35766-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="35766-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35766-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35766-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35766-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="35766-112">See Also</span></span>  
 

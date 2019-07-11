---
title: IObjectHandle::Unwrap 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc5bed553ac54eb708beae23f5c29cbedcb2b4e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749073"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="13cac-102">IObjectHandle::Unwrap 方法</span><span class="sxs-lookup"><span data-stu-id="13cac-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="13cac-103">解除包裝從間接取值的傳值方式封送處理物件。</span><span class="sxs-lookup"><span data-stu-id="13cac-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13cac-104">語法</span><span class="sxs-lookup"><span data-stu-id="13cac-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13cac-105">參數</span><span class="sxs-lookup"><span data-stu-id="13cac-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="13cac-106">[out]要未包裝的物件指標。</span><span class="sxs-lookup"><span data-stu-id="13cac-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13cac-107">需求</span><span class="sxs-lookup"><span data-stu-id="13cac-107">Requirements</span></span>  
 <span data-ttu-id="13cac-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13cac-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13cac-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13cac-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13cac-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="13cac-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13cac-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13cac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

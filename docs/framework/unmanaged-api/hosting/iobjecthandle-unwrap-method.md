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
ms.openlocfilehash: 4c18607d5373b415228846350a3dd0637ade1b45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917586"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="df226-102">IObjectHandle::Unwrap 方法</span><span class="sxs-lookup"><span data-stu-id="df226-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="df226-103">解除包裝從間接取值的傳值方式封送處理物件。</span><span class="sxs-lookup"><span data-stu-id="df226-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df226-104">語法</span><span class="sxs-lookup"><span data-stu-id="df226-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df226-105">參數</span><span class="sxs-lookup"><span data-stu-id="df226-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="df226-106">[out]要未包裝的物件指標。</span><span class="sxs-lookup"><span data-stu-id="df226-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df226-107">需求</span><span class="sxs-lookup"><span data-stu-id="df226-107">Requirements</span></span>  
 <span data-ttu-id="df226-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="df226-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df226-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df226-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df226-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="df226-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df226-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df226-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

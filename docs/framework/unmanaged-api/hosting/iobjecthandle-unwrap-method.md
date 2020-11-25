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
ms.openlocfilehash: 32b6d2c05a96658ab2b8ec1df288d2be05bb947f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730660"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="9cd1f-102">IObjectHandle::Unwrap 方法</span><span class="sxs-lookup"><span data-stu-id="9cd1f-102">IObjectHandle::Unwrap Method</span></span>

<span data-ttu-id="9cd1f-103">從間接取值解除封送處理傳值的物件。</span><span class="sxs-lookup"><span data-stu-id="9cd1f-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cd1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9cd1f-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cd1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="9cd1f-105">Parameters</span></span>  

 `ppv`  
 <span data-ttu-id="9cd1f-106">擴展要解除包裝之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="9cd1f-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cd1f-107">需求</span><span class="sxs-lookup"><span data-stu-id="9cd1f-107">Requirements</span></span>  

 <span data-ttu-id="9cd1f-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9cd1f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cd1f-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9cd1f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cd1f-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="9cd1f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cd1f-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cd1f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

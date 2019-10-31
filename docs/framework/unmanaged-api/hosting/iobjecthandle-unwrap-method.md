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
ms.openlocfilehash: be488ebe663169cabc5b569335dfc784fdf30556
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102686"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="5b698-102">IObjectHandle::Unwrap 方法</span><span class="sxs-lookup"><span data-stu-id="5b698-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="5b698-103">從間接取值解除封送處理傳值物件。</span><span class="sxs-lookup"><span data-stu-id="5b698-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b698-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b698-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b698-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b698-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="5b698-106">脫銷要解除包裝之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="5b698-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b698-107">需求</span><span class="sxs-lookup"><span data-stu-id="5b698-107">Requirements</span></span>  
 <span data-ttu-id="5b698-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b698-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b698-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5b698-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b698-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5b698-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b698-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b698-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

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
ms.openlocfilehash: 0ff088731514b2da0d8b1fa51ef48d8b71d16528
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842227"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="0ab92-102">IObjectHandle::Unwrap 方法</span><span class="sxs-lookup"><span data-stu-id="0ab92-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="0ab92-103">從間接取值解除封送處理傳值物件。</span><span class="sxs-lookup"><span data-stu-id="0ab92-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab92-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ab92-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ab92-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ab92-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="0ab92-106">脫銷要解除包裝之物件的指標。</span><span class="sxs-lookup"><span data-stu-id="0ab92-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ab92-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="0ab92-107">Requirements</span></span>  
 <span data-ttu-id="0ab92-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ab92-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab92-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="0ab92-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ab92-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0ab92-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ab92-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab92-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

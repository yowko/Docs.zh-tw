---
title: ICorPublishEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: e9f7f1fc0f04e8cc8c69d533c1dbba380d04ebfb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140494"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="a2c9d-102">ICorPublishEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="a2c9d-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="a2c9d-103">建立這個[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)物件的複本。</span><span class="sxs-lookup"><span data-stu-id="a2c9d-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2c9d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2c9d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2c9d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a2c9d-106">脫銷這個 `ICorPublishEnum` 物件之複本的 `ICorPublishEnum` 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="a2c9d-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2c9d-107">需求</span><span class="sxs-lookup"><span data-stu-id="a2c9d-107">Requirements</span></span>  
 <span data-ttu-id="a2c9d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2c9d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2c9d-109">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="a2c9d-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a2c9d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2c9d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2c9d-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2c9d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c9d-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2c9d-112">See also</span></span>

- [<span data-ttu-id="a2c9d-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a2c9d-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0ce1d8c0074f62d35e16465b368269e233a713b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105127"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="ab366-102">ICorPublishEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="ab366-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="ab366-103">建立一份這[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="ab366-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab366-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab366-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab366-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab366-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="ab366-106">[out]位址指標`ICorPublishEnum`物件，這個複本`ICorPublishEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="ab366-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab366-107">需求</span><span class="sxs-lookup"><span data-stu-id="ab366-107">Requirements</span></span>  
 <span data-ttu-id="ab366-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab366-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab366-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ab366-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ab366-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab366-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab366-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab366-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab366-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab366-112">See also</span></span>

- [<span data-ttu-id="ab366-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ab366-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

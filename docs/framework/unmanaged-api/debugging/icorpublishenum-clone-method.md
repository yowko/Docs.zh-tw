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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105127"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="34451-102">ICorPublishEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="34451-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="34451-103">建立一份這[ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="34451-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34451-104">語法</span><span class="sxs-lookup"><span data-stu-id="34451-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34451-105">參數</span><span class="sxs-lookup"><span data-stu-id="34451-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="34451-106">[out]位址指標`ICorPublishEnum`物件，這個複本`ICorPublishEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="34451-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34451-107">需求</span><span class="sxs-lookup"><span data-stu-id="34451-107">Requirements</span></span>  
 <span data-ttu-id="34451-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34451-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34451-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="34451-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="34451-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34451-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="34451-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="34451-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34451-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34451-112">See also</span></span>

- [<span data-ttu-id="34451-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="34451-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

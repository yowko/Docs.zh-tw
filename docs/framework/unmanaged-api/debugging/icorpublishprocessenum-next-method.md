---
title: ICorPublishProcessEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19a10a527c37d93d00bec799fdaa12bb0ad3fdbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423867"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="36e38-102">ICorPublishProcessEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="36e38-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="36e38-103">從集合中，從目前游標位置開始，取得指定的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="36e38-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36e38-104">語法</span><span class="sxs-lookup"><span data-stu-id="36e38-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36e38-105">參數</span><span class="sxs-lookup"><span data-stu-id="36e38-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="36e38-106">[in]要擷取的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="36e38-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="36e38-107">[out]陣列指標擷取[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件，其中每一個都代表一個程序。</span><span class="sxs-lookup"><span data-stu-id="36e38-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="36e38-108">[out]指向實際傳回的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="36e38-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="36e38-109">這個值可以是 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="36e38-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36e38-110">需求</span><span class="sxs-lookup"><span data-stu-id="36e38-110">Requirements</span></span>  
 <span data-ttu-id="36e38-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36e38-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36e38-112">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="36e38-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="36e38-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36e38-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36e38-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36e38-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36e38-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36e38-115">See Also</span></span>  
 [<span data-ttu-id="36e38-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="36e38-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)

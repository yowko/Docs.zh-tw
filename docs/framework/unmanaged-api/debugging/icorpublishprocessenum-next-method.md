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
ms.openlocfilehash: 40a6376d4f4ffd09743441df1965d0a0f0d969b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764849"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="dbae9-102">ICorPublishProcessEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="dbae9-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="dbae9-103">從集合中，從目前游標位置開始，取得指定的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="dbae9-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbae9-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbae9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbae9-105">參數</span><span class="sxs-lookup"><span data-stu-id="dbae9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dbae9-106">[in]要擷取的處理序數目。</span><span class="sxs-lookup"><span data-stu-id="dbae9-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="dbae9-107">[out]擷取陣列的指標[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)物件，每一個都代表一個程序。</span><span class="sxs-lookup"><span data-stu-id="dbae9-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dbae9-108">[out]實際傳回的處理序數目的指標。</span><span class="sxs-lookup"><span data-stu-id="dbae9-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="dbae9-109">此值可能為 null 如果`celt`是其中一個。</span><span class="sxs-lookup"><span data-stu-id="dbae9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbae9-110">需求</span><span class="sxs-lookup"><span data-stu-id="dbae9-110">Requirements</span></span>  
 <span data-ttu-id="dbae9-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dbae9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbae9-112">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="dbae9-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="dbae9-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbae9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbae9-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbae9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbae9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbae9-115">See also</span></span>

- [<span data-ttu-id="dbae9-116">ICorPublishProcessEnum 介面</span><span class="sxs-lookup"><span data-stu-id="dbae9-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)

---
title: ICorPublishEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9be0c3b931130e0ea86766b5134ca514478f0201
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764937"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="e6013-102">ICorPublishEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="e6013-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="e6013-103">將游標移往前列舉中所指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="e6013-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6013-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6013-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6013-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6013-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e6013-106">[in]用來將游標向前移動的項目數目。</span><span class="sxs-lookup"><span data-stu-id="e6013-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6013-107">需求</span><span class="sxs-lookup"><span data-stu-id="e6013-107">Requirements</span></span>  
 <span data-ttu-id="e6013-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6013-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6013-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e6013-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e6013-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6013-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6013-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6013-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6013-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6013-112">See also</span></span>

- [<span data-ttu-id="e6013-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e6013-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

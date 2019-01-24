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
ms.openlocfilehash: 4e7d4e449624f295c4011a4ccdad46226e742a8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681153"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="58f69-102">ICorPublishEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="58f69-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="58f69-103">將游標移往前列舉中所指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="58f69-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58f69-104">語法</span><span class="sxs-lookup"><span data-stu-id="58f69-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58f69-105">參數</span><span class="sxs-lookup"><span data-stu-id="58f69-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="58f69-106">[in]用來將游標向前移動的項目數目。</span><span class="sxs-lookup"><span data-stu-id="58f69-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58f69-107">需求</span><span class="sxs-lookup"><span data-stu-id="58f69-107">Requirements</span></span>  
 <span data-ttu-id="58f69-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58f69-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58f69-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="58f69-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="58f69-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58f69-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58f69-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58f69-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58f69-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58f69-112">See also</span></span>
- [<span data-ttu-id="58f69-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="58f69-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

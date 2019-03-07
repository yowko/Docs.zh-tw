---
title: ICorPublishEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c353edf9db0a7bc7ec0a25f712527dc3c9d8cc28
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484650"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="cb5c7-102">ICorPublishEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="cb5c7-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="cb5c7-103">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="cb5c7-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb5c7-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb5c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb5c7-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="cb5c7-106">[out]列舉中的項目數目指標。</span><span class="sxs-lookup"><span data-stu-id="cb5c7-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5c7-107">需求</span><span class="sxs-lookup"><span data-stu-id="cb5c7-107">Requirements</span></span>  
 <span data-ttu-id="cb5c7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb5c7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5c7-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="cb5c7-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cb5c7-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb5c7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb5c7-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5c7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5c7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb5c7-112">See also</span></span>
- [<span data-ttu-id="cb5c7-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="cb5c7-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

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
ms.openlocfilehash: 0424d929f40da1faabd7456cdd85e39a59246d48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103242"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="ea904-102">ICorPublishEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="ea904-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="ea904-103">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="ea904-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea904-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea904-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea904-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea904-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="ea904-106">[out]列舉中的項目數目指標。</span><span class="sxs-lookup"><span data-stu-id="ea904-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea904-107">需求</span><span class="sxs-lookup"><span data-stu-id="ea904-107">Requirements</span></span>  
 <span data-ttu-id="ea904-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea904-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea904-109">**標頭：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ea904-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ea904-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea904-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea904-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea904-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea904-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea904-112">See also</span></span>

- [<span data-ttu-id="ea904-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ea904-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

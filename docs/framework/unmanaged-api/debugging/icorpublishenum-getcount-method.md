---
title: "ICorPublishEnum::GetCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.GetCount
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 023965489530e70deb7dc9460418ef0d56654081
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="f53eb-102">ICorPublishEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="f53eb-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="f53eb-103">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="f53eb-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f53eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="f53eb-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f53eb-105">參數</span><span class="sxs-lookup"><span data-stu-id="f53eb-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="f53eb-106">[out]列舉中的項目編號的指標。</span><span class="sxs-lookup"><span data-stu-id="f53eb-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f53eb-107">需求</span><span class="sxs-lookup"><span data-stu-id="f53eb-107">Requirements</span></span>  
 <span data-ttu-id="f53eb-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f53eb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f53eb-109">**標頭：** CorPub.idl、 CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f53eb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f53eb-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f53eb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f53eb-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f53eb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f53eb-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="f53eb-112">See Also</span></span>  
 [<span data-ttu-id="f53eb-113">ICorPublishEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f53eb-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

---
title: GetIdentityAuthority 函式
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3090887d3c670b2784b7b40c7d63832715596c3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697598"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="84977-102">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="84977-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="84977-103">取得指標[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理程式碼物件的索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="84977-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84977-104">語法</span><span class="sxs-lookup"><span data-stu-id="84977-104">Syntax</span></span>  
  
```  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="84977-105">參數</span><span class="sxs-lookup"><span data-stu-id="84977-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="84977-106">[out]傳回`IIdentityAuthority`指標。</span><span class="sxs-lookup"><span data-stu-id="84977-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84977-107">需求</span><span class="sxs-lookup"><span data-stu-id="84977-107">Requirements</span></span>  
 <span data-ttu-id="84977-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84977-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84977-109">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="84977-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="84977-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84977-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84977-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84977-111">See also</span></span>

- [<span data-ttu-id="84977-112">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="84977-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="84977-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="84977-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

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
ms.openlocfilehash: c5e8dd4a9dbf301b0910eda220513e9a3ffdc1cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778647"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="09a96-102">GetIdentityAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="09a96-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="09a96-103">取得指標[IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)管理程式碼物件的索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="09a96-103">Gets a pointer to an [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a96-104">語法</span><span class="sxs-lookup"><span data-stu-id="09a96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="09a96-105">參數</span><span class="sxs-lookup"><span data-stu-id="09a96-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="09a96-106">[out]傳回`IIdentityAuthority`指標。</span><span class="sxs-lookup"><span data-stu-id="09a96-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09a96-107">需求</span><span class="sxs-lookup"><span data-stu-id="09a96-107">Requirements</span></span>  
 <span data-ttu-id="09a96-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09a96-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a96-109">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="09a96-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="09a96-110">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a96-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a96-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09a96-111">See also</span></span>

- [<span data-ttu-id="09a96-112">IIdentityAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="09a96-112">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)
- [<span data-ttu-id="09a96-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="09a96-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

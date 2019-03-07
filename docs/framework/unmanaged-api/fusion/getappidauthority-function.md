---
title: GetAppIdAuthority 函式
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162341ee8cb27e5edc455207bbe094356c5167e7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466072"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="2cb28-102">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="2cb28-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="2cb28-103">取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式身分識別和參考的索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2cb28-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb28-104">語法</span><span class="sxs-lookup"><span data-stu-id="2cb28-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cb28-105">參數</span><span class="sxs-lookup"><span data-stu-id="2cb28-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="2cb28-106">[out]傳回`IAppIdAuthority`指標。</span><span class="sxs-lookup"><span data-stu-id="2cb28-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb28-107">需求</span><span class="sxs-lookup"><span data-stu-id="2cb28-107">Requirements</span></span>  
 <span data-ttu-id="2cb28-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cb28-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb28-109">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="2cb28-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="2cb28-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb28-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb28-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cb28-111">See also</span></span>
- [<span data-ttu-id="2cb28-112">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="2cb28-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)
- [<span data-ttu-id="2cb28-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2cb28-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

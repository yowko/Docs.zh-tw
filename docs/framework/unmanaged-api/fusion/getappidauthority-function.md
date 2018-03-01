---
title: "GetAppIdAuthority 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e89624feb04050534b917b865d5cb53b8c4cf58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getappidauthority-function"></a><span data-ttu-id="81a55-102">GetAppIdAuthority 函式</span><span class="sxs-lookup"><span data-stu-id="81a55-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="81a55-103">取得指標[IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)管理應用程式識別與參考索引鍵的執行個體。</span><span class="sxs-lookup"><span data-stu-id="81a55-103">Gets a pointer to an [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a55-104">語法</span><span class="sxs-lookup"><span data-stu-id="81a55-104">Syntax</span></span>  
  
```  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81a55-105">參數</span><span class="sxs-lookup"><span data-stu-id="81a55-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="81a55-106">[out]傳回`IAppIdAuthority`指標。</span><span class="sxs-lookup"><span data-stu-id="81a55-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a55-107">需求</span><span class="sxs-lookup"><span data-stu-id="81a55-107">Requirements</span></span>  
 <span data-ttu-id="81a55-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81a55-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a55-109">**標頭：** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="81a55-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="81a55-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a55-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a55-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="81a55-111">See Also</span></span>  
 [<span data-ttu-id="81a55-112">IAppIdAuthority 介面</span><span class="sxs-lookup"><span data-stu-id="81a55-112">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 [<span data-ttu-id="81a55-113">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="81a55-113">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

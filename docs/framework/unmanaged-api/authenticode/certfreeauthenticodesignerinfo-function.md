---
title: "CertFreeAuthenticodeSignerInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeSignerInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8b38d30a1323d0d44330b8bb9a006c372ea7780
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="b0558-102">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="b0558-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="b0558-103">釋出配置給資源[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="b0558-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0558-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0558-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0558-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0558-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="b0558-106">[in, out] 所要發行的簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="b0558-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="b0558-107">請參閱[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="b0558-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0558-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="b0558-108">Return Value</span></span>  
 <span data-ttu-id="b0558-109">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="b0558-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="b0558-110">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="b0558-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0558-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0558-111">See Also</span></span>  
 [<span data-ttu-id="b0558-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b0558-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

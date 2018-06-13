---
title: CertFreeAuthenticodeSignerInfo 函式
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f15dc49d14e781f69d0f9da8f314eb71d8c034
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401612"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="e549b-102">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="e549b-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="e549b-103">釋出配置給資源[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="e549b-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e549b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e549b-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e549b-105">參數</span><span class="sxs-lookup"><span data-stu-id="e549b-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="e549b-106">[in, out] 所要發行的簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="e549b-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="e549b-107">請參閱[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="e549b-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e549b-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e549b-108">Return Value</span></span>  
 <span data-ttu-id="e549b-109">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="e549b-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="e549b-110">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e549b-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e549b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e549b-111">See Also</span></span>  
 [<span data-ttu-id="e549b-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e549b-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

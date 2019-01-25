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
ms.openlocfilehash: 4282be8e57c965e14398a9284002b1191c5169fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708034"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="9babd-102">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="9babd-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="9babd-103">釋出配置給資源[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="9babd-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9babd-104">語法</span><span class="sxs-lookup"><span data-stu-id="9babd-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9babd-105">參數</span><span class="sxs-lookup"><span data-stu-id="9babd-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="9babd-106">[in, out] 所要發行的簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="9babd-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="9babd-107">請參閱[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="9babd-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9babd-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9babd-108">Return Value</span></span>  
 <span data-ttu-id="9babd-109">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="9babd-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="9babd-110">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9babd-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9babd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9babd-111">See also</span></span>
- [<span data-ttu-id="9babd-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9babd-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

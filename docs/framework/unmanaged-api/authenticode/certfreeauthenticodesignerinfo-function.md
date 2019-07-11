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
ms.openlocfilehash: 42f5685a9a976be7a3a73badf286f77216e43106
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741239"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="2c2b5-102">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="2c2b5-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="2c2b5-103">釋出配置給資源[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="2c2b5-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c2b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c2b5-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c2b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c2b5-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="2c2b5-106">[in, out] 所要發行的簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="2c2b5-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="2c2b5-107">請參閱[AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="2c2b5-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c2b5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2c2b5-108">Return Value</span></span>  
 <span data-ttu-id="2c2b5-109">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="2c2b5-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="2c2b5-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2c2b5-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2b5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c2b5-111">See also</span></span>

- [<span data-ttu-id="2c2b5-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2c2b5-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

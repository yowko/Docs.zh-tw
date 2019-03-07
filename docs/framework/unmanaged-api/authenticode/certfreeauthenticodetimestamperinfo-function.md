---
title: CertFreeAuthenticodeTimestamperInfo 函式
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082ed24eb65de12f337ab4a379b088da0f6eea5a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497375"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="27c69-102">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="27c69-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="27c69-103">釋出配置給資源[AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="27c69-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27c69-104">語法</span><span class="sxs-lookup"><span data-stu-id="27c69-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27c69-105">參數</span><span class="sxs-lookup"><span data-stu-id="27c69-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="27c69-106">[in, out] 所要發行的時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="27c69-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="27c69-107">請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="27c69-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27c69-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="27c69-108">Return Value</span></span>  
 <span data-ttu-id="27c69-109">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="27c69-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="27c69-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="27c69-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27c69-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27c69-111">See also</span></span>
- [<span data-ttu-id="27c69-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="27c69-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

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
ms.openlocfilehash: 27c16cb5d85ddffc1646bee893c5644682812025
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560577"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="f757d-102">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="f757d-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="f757d-103">釋出配置給資源[AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="f757d-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f757d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f757d-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f757d-105">參數</span><span class="sxs-lookup"><span data-stu-id="f757d-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="f757d-106">[in, out] 所要發行的時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="f757d-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="f757d-107">請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="f757d-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f757d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="f757d-108">Return Value</span></span>  
 <span data-ttu-id="f757d-109">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f757d-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="f757d-110">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f757d-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f757d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f757d-111">See also</span></span>
- [<span data-ttu-id="f757d-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f757d-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

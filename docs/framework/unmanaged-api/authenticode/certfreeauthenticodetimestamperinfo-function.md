---
title: "CertFreeAuthenticodeTimestamperInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertFreeAuthenticodeTimestamperInfo
api_location: clr.dll
api_type: DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8b6392e57e641d25d07580fcb6bf630f8d983be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="88f94-102">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="88f94-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="88f94-103">釋出配置給資源[AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="88f94-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f94-104">語法</span><span class="sxs-lookup"><span data-stu-id="88f94-104">Syntax</span></span>  
  
```  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88f94-105">參數</span><span class="sxs-lookup"><span data-stu-id="88f94-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="88f94-106">[in, out] 所要發行的時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="88f94-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="88f94-107">請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="88f94-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88f94-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="88f94-108">Return Value</span></span>  
 <span data-ttu-id="88f94-109">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="88f94-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="88f94-110">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="88f94-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f94-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88f94-111">See Also</span></span>  
 [<span data-ttu-id="88f94-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="88f94-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

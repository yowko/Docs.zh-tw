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
ms.openlocfilehash: a8ecada29528b065ddad0abc80a850ee0f347f6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787000"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="9f407-102">CertFreeAuthenticodeTimestamperInfo 函式</span><span class="sxs-lookup"><span data-stu-id="9f407-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>
<span data-ttu-id="9f407-103">釋放配置給[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)結構的資源。</span><span class="sxs-lookup"><span data-stu-id="9f407-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f407-104">語法</span><span class="sxs-lookup"><span data-stu-id="9f407-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f407-105">參數</span><span class="sxs-lookup"><span data-stu-id="9f407-105">Parameters</span></span>  
 `pTimestamperInfo`  
 <span data-ttu-id="9f407-106">[in, out] 所要發行的時間戳記程式資訊。</span><span class="sxs-lookup"><span data-stu-id="9f407-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="9f407-107">請參閱[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="9f407-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f407-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="9f407-108">Return Value</span></span>  
 <span data-ttu-id="9f407-109">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="9f407-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="9f407-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9f407-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f407-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f407-111">See also</span></span>

- [<span data-ttu-id="9f407-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9f407-112">Authenticode</span></span>](index.md)

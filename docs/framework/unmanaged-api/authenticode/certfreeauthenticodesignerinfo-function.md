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
ms.openlocfilehash: 357a2ca0ffc733adb14a21624cbe28fb754c8240
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776723"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="7f4d0-102">CertFreeAuthenticodeSignerInfo 函式</span><span class="sxs-lookup"><span data-stu-id="7f4d0-102">CertFreeAuthenticodeSignerInfo Function</span></span>
<span data-ttu-id="7f4d0-103">釋放配置給[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)結構的資源。</span><span class="sxs-lookup"><span data-stu-id="7f4d0-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f4d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f4d0-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f4d0-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f4d0-105">Parameters</span></span>  
 `pSignerInfo`  
 <span data-ttu-id="7f4d0-106">[in, out] 所要發行的簽署人資訊。</span><span class="sxs-lookup"><span data-stu-id="7f4d0-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="7f4d0-107">請參閱[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="7f4d0-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f4d0-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="7f4d0-108">Return Value</span></span>  
 <span data-ttu-id="7f4d0-109">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="7f4d0-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="7f4d0-110">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="7f4d0-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f4d0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f4d0-111">See also</span></span>

- [<span data-ttu-id="7f4d0-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="7f4d0-112">Authenticode</span></span>](index.md)

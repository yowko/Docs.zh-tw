---
title: _AxlGetIssuerPublicKeyHash 函式
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408b71bf38427d12418e05f8b509fe841bc95ef1
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42754528"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="e1710-102">_AxlGetIssuerPublicKeyHash 函式</span><span class="sxs-lookup"><span data-stu-id="e1710-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="e1710-103">擷取公開金鑰的 SHA-1 雜湊，此公開金鑰與用於簽署特定憑證的私密金鑰相關。</span><span class="sxs-lookup"><span data-stu-id="e1710-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1710-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1710-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1710-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1710-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="e1710-106">[in] CSP 公開金鑰 Blob。</span><span class="sxs-lookup"><span data-stu-id="e1710-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="e1710-107">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="e1710-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="e1710-108">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="e1710-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1710-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1710-109">Return Value</span></span>  
 <span data-ttu-id="e1710-110">若函式成功則傳回 `S_OK`：反之則傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="e1710-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1710-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1710-111">See Also</span></span>  
 [<span data-ttu-id="e1710-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e1710-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

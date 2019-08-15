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
ms.openlocfilehash: 1cfc2f5cde22bf63275dd4bdc65857ac1d51b3fe
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038424"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="529a4-102">\_AxlGetIssuerPublicKeyHash 函式</span><span class="sxs-lookup"><span data-stu-id="529a4-102">\_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="529a4-103">擷取公開金鑰的 SHA-1 雜湊，該公開金鑰與用來簽署指定憑證的私密金鑰相關聯。</span><span class="sxs-lookup"><span data-stu-id="529a4-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="529a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="529a4-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="529a4-105">參數</span><span class="sxs-lookup"><span data-stu-id="529a4-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="529a4-106">[in] CSP 公開金鑰 Blob。</span><span class="sxs-lookup"><span data-stu-id="529a4-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="529a4-107">請參閱[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="529a4-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="529a4-108">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="529a4-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="529a4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="529a4-109">Return Value</span></span>  
 <span data-ttu-id="529a4-110">如果函式成功，會傳回 `S_OK`，否則會傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="529a4-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529a4-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="529a4-111">See also</span></span>

- [<span data-ttu-id="529a4-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="529a4-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

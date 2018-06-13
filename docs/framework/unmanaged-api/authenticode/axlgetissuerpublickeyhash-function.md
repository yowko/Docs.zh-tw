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
ms.openlocfilehash: b197aa539e60a9dbcee55cf190c44b45da3a5fb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402011"
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="68d9a-102">_AxlGetIssuerPublicKeyHash 函式</span><span class="sxs-lookup"><span data-stu-id="68d9a-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="68d9a-103">擷取公開金鑰的 SHA-1 雜湊，此公開金鑰與用於簽署特定憑證的私密金鑰相關。</span><span class="sxs-lookup"><span data-stu-id="68d9a-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d9a-104">語法</span><span class="sxs-lookup"><span data-stu-id="68d9a-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68d9a-105">參數</span><span class="sxs-lookup"><span data-stu-id="68d9a-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="68d9a-106">[in] CSP 公開金鑰 Blob。</span><span class="sxs-lookup"><span data-stu-id="68d9a-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="68d9a-107">請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="68d9a-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="68d9a-108">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="68d9a-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68d9a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="68d9a-109">Return Value</span></span>  
 <span data-ttu-id="68d9a-110">若函式成功則傳回 `S_OK`：反之則傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="68d9a-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68d9a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68d9a-111">See Also</span></span>  
 [<span data-ttu-id="68d9a-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="68d9a-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

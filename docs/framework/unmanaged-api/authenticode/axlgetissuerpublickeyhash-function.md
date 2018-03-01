---
title: "_AxlGetIssuerPublicKeyHash 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fee2b3e0e74ec13009a9b02d226c6a99b0e2f34b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="da12e-102">_AxlGetIssuerPublicKeyHash 函式</span><span class="sxs-lookup"><span data-stu-id="da12e-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="da12e-103">擷取公開金鑰的 SHA-1 雜湊，此公開金鑰與用於簽署特定憑證的私密金鑰相關。</span><span class="sxs-lookup"><span data-stu-id="da12e-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da12e-104">語法</span><span class="sxs-lookup"><span data-stu-id="da12e-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da12e-105">參數</span><span class="sxs-lookup"><span data-stu-id="da12e-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="da12e-106">[in] CSP 公開金鑰 Blob。</span><span class="sxs-lookup"><span data-stu-id="da12e-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="da12e-107">請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="da12e-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="da12e-108">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="da12e-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da12e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="da12e-109">Return Value</span></span>  
 <span data-ttu-id="da12e-110">若函式成功則傳回 `S_OK`：反之則傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="da12e-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da12e-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="da12e-111">See Also</span></span>  
 [<span data-ttu-id="da12e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="da12e-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

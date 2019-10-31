---
title: _AxlPublicKeyBlobToPublicKeyToken 函式
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099899"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="063cf-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span><span class="sxs-lookup"><span data-stu-id="063cf-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="063cf-103">從 CSP PUBLICKEYBLOB 格式運算強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="063cf-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="063cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="063cf-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="063cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="063cf-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="063cf-106">[in] CSP 公開金鑰 Blob。</span><span class="sxs-lookup"><span data-stu-id="063cf-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="063cf-107">[out] WCHAR \* 的指標，可接收十六進位編碼公開金鑰雜湊。</span><span class="sxs-lookup"><span data-stu-id="063cf-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="063cf-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="063cf-108">Return Value</span></span>  
 <span data-ttu-id="063cf-109">如果函式成功，會傳回 `S_OK`，否則會傳回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="063cf-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063cf-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="063cf-110">See also</span></span>

- [<span data-ttu-id="063cf-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="063cf-111">Authenticode</span></span>](index.md)

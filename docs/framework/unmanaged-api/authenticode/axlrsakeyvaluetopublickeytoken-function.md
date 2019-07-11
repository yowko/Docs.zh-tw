---
title: _AxlRSAKeyValueToPublicKeyToken 函式
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f9981c4cf2e45795576024b797f93831324dbc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741262"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="d550b-102">\_AxlRSAKeyValueToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="d550b-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="d550b-103">將模數和指數轉換成強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d550b-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d550b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d550b-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d550b-105">參數</span><span class="sxs-lookup"><span data-stu-id="d550b-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="d550b-106">[in]Base64 編碼的模數 blob (從\<模數 > 項目)。</span><span class="sxs-lookup"><span data-stu-id="d550b-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="d550b-107">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="d550b-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="d550b-108">[in]Base64 編碼的指數 blob (從\<指數 > 項目)。</span><span class="sxs-lookup"><span data-stu-id="d550b-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="d550b-109">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="d550b-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="d550b-110">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="d550b-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d550b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d550b-111">Return Value</span></span>  
 <span data-ttu-id="d550b-112">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="d550b-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="d550b-113">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d550b-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d550b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d550b-114">See also</span></span>

- [<span data-ttu-id="d550b-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="d550b-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

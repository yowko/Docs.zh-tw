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
ms.openlocfilehash: 49476a4417e5431842f8e2ba0371c53c5c9f03e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948889"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="f501d-102">\_AxlRSAKeyValueToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="f501d-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="f501d-103">將模數和指數轉換成強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f501d-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f501d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f501d-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f501d-105">參數</span><span class="sxs-lookup"><span data-stu-id="f501d-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="f501d-106">[in]Base64 編碼的模數 blob (從\<模數 > 項目)。</span><span class="sxs-lookup"><span data-stu-id="f501d-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="f501d-107">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="f501d-107">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="f501d-108">[in]Base64 編碼的指數 blob (從\<指數 > 項目)。</span><span class="sxs-lookup"><span data-stu-id="f501d-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="f501d-109">請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="f501d-109">See the [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="f501d-110">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="f501d-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f501d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="f501d-111">Return Value</span></span>  
 <span data-ttu-id="f501d-112">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="f501d-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="f501d-113">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="f501d-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f501d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f501d-114">See also</span></span>

- [<span data-ttu-id="f501d-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f501d-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

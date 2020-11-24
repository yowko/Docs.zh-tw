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
ms.openlocfilehash: 5c1e2bfc7fd55e807af68744e28faa473daea772
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674212"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="887b1-102">\_AxlRSAKeyValueToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="887b1-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="887b1-103">將模數和指數轉換成強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="887b1-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="887b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="887b1-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="887b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="887b1-105">Parameters</span></span>  

 `pModulusBlob`  
 <span data-ttu-id="887b1-106">在Base64 編碼的模數 blob (自 \<Modulus> 元素) 。</span><span class="sxs-lookup"><span data-stu-id="887b1-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="887b1-107">請參閱 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) 結構。</span><span class="sxs-lookup"><span data-stu-id="887b1-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="887b1-108">在Base64 編碼的指數 blob (自 \<Exponent> 元素) 。</span><span class="sxs-lookup"><span data-stu-id="887b1-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="887b1-109">請參閱 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) 結構。</span><span class="sxs-lookup"><span data-stu-id="887b1-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="887b1-110">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="887b1-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="887b1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="887b1-111">Return Value</span></span>  

 <span data-ttu-id="887b1-112">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="887b1-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="887b1-113">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="887b1-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887b1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="887b1-114">See also</span></span>

- [<span data-ttu-id="887b1-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="887b1-115">Authenticode</span></span>](index.md)

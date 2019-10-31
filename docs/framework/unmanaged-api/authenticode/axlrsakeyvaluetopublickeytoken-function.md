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
ms.openlocfilehash: 1f53df33a65d3f75b7574eda3507e370c2e086ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099823"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="8420b-102">\_AxlRSAKeyValueToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="8420b-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="8420b-103">將模數和指數轉換成強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8420b-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8420b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8420b-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8420b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8420b-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="8420b-106">在Base64 編碼的模數 blob （來自 \<模數 > 元素）。</span><span class="sxs-lookup"><span data-stu-id="8420b-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="8420b-107">請參閱[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="8420b-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="8420b-108">在Base64 編碼的指數 blob （從 \<指數 > 元素）。</span><span class="sxs-lookup"><span data-stu-id="8420b-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="8420b-109">請參閱[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)結構。</span><span class="sxs-lookup"><span data-stu-id="8420b-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="8420b-110">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="8420b-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8420b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8420b-111">Return Value</span></span>  
 <span data-ttu-id="8420b-112">如果函式成功，會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="8420b-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="8420b-113">否則會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8420b-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8420b-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8420b-114">See also</span></span>

- [<span data-ttu-id="8420b-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8420b-115">Authenticode</span></span>](index.md)

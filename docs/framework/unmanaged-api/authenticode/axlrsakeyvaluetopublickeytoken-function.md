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
ms.openlocfilehash: 7ef73f0f7599fdff887437756a5995591fd8ec89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402404"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="cc2dd-102">_AxlRSAKeyValueToPublicKeyToken 函式</span><span class="sxs-lookup"><span data-stu-id="cc2dd-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="cc2dd-103">將模數及指數轉換為強式名稱公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc2dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc2dd-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cc2dd-105">參數</span><span class="sxs-lookup"><span data-stu-id="cc2dd-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="cc2dd-106">[in]Base64 編碼的模數 blob (來自\<模數 > 項目)。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="cc2dd-107">請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="cc2dd-108">[in]Base64 編碼的指數 blob (來自\<指數 > 項目)。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="cc2dd-109">請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="cc2dd-110">[out] WCHAR \* (要接收十六進位編碼的公開金鑰語彙基元) 的指標。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc2dd-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="cc2dd-111">Return Value</span></span>  
 <span data-ttu-id="cc2dd-112">若函式成功則傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="cc2dd-113">反之則傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cc2dd-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc2dd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc2dd-114">See Also</span></span>  
 [<span data-ttu-id="cc2dd-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="cc2dd-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)

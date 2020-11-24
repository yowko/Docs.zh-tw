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
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken 函式

將模數和指數轉換成強式名稱公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>參數  

 `pModulusBlob`  
 在Base64 編碼的模數 blob (自 \<Modulus> 元素) 。  請參閱 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) 結構。  
  
 `pExponentBlob`  
 在Base64 編碼的指數 blob (自 \<Exponent> 元素) 。 請參閱 [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) 結構。  
  
 `ppwszPublicKeyToken`  
 [out] WCHAR * (要接收十六進位編碼的公開金鑰語彙基元) 的指標。  
  
## <a name="return-value"></a>傳回值  

 如果函式成功，會傳回 `S_OK`。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](index.md)

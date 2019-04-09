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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207821"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken 函式

將模數和指數轉換成強式名稱公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `pModulusBlob`  
 [in]Base64 編碼的模數 blob (從\<模數 > 項目)。  請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。  
  
 `pExponentBlob`  
 [in]Base64 編碼的指數 blob (從\<指數 > 項目)。 請參閱[CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob)結構。  
  
 `ppwszPublicKeyToken`  
 [out] WCHAR * (要接收十六進位編碼的公開金鑰語彙基元) 的指標。  
  
## <a name="return-value"></a>傳回值  
 `S_OK` 如果函式成功。 否則會傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)

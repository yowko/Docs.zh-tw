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
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>_AxlRSAKeyValueToPublicKeyToken 函式
將模數及指數轉換為強式名稱公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pModulusBlob`  
 [in]Base64 編碼的模數 blob (來自\<模數 > 項目)。  請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。  
  
 `pExponentBlob`  
 [in]Base64 編碼的指數 blob (來自\<指數 > 項目)。 請參閱[CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx)結構。  
  
 `ppwszPublicKeyToken`  
 [out] WCHAR * (要接收十六進位編碼的公開金鑰語彙基元) 的指標。  
  
## <a name="return-value"></a>傳回值  
 若函式成功則傳回 `S_OK`。 反之則傳回錯誤碼。  
  
## <a name="see-also"></a>另請參閱  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)

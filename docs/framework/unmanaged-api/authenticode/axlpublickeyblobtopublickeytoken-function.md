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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56333165d179abd79e82f1416342a2700029eb12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>_AxlPublicKeyBlobToPublicKeyToken 函式
從 CSP PUBLICKEYBLOB 格式運算強式名稱公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pCspPublicKeyBlob`  
 [in] CSP 公開金鑰 Blob。  
  
 `ppwszPublicKeyHash`  
 [out] WCHAR * 的指標，可接收十六進位編碼公開金鑰雜湊。  
  
## <a name="return-value"></a>傳回值  
 若函式成功則傳回 `S_OK`：反之則傳回 `S_FALSE`。  
  
## <a name="see-also"></a>另請參閱  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)

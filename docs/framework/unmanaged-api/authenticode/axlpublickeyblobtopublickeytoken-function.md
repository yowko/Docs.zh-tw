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
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_AxlPublicKeyBlobToPublicKeyToken Function
從 CSP PUBLICKEYBLOB 格式運算強式名稱公開金鑰語彙基元。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>參數  
 `pCspPublicKeyBlob`  
 [in] CSP 公開金鑰 Blob。  
  
 `ppwszPublicKeyHash`  
 [out] WCHAR * 的指標，可接收十六進位編碼公開金鑰雜湊。  
  
## <a name="return-value"></a>傳回值  
 如果函式成功，會傳回 `S_OK`，否則會傳回 `S_FALSE`。  
  
## <a name="see-also"></a>請參閱

- [Authenticode](index.md)

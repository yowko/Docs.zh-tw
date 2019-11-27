---
title: GetPublicKeyToken 方法
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: 2e7ed4e1529104db30b0b06665f74342d9ca9a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447238"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken 方法
抓取指定的 keyfile 或金鑰容器的公開金鑰 token。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a>參數  
 `pszKeyFile`  
 金鑰的檔案名。  
  
 `pszKeyContainer`  
 金鑰容器的名稱。  
  
 `pvPublicKeyToken`  
 要儲存金鑰 token 的位址。  
  
 `pcbPublicKeyToken`  
 指定 `pvPublicKeyToken`所指示的緩衝區大小（以位元組為單位）。 傳回時，包含實際使用的位元組數目。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功，則傳回 S_OK。  
  
## <a name="requirements"></a>需求  
 需要 alink. h。  
  
## <a name="see-also"></a>另請參閱

- [IALink2 介面](ialink2-interface.md)
- [IALink 介面](ialink-interface.md)
- [ALink API](index.md)
